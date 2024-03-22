<!-- MyComponent.svelte -->
<script lang="ts">
	import { onMount } from 'svelte';
	import { cityName } from '../../store/cityName';
	import { weatherData } from '../../store/weatherStore';
	import { forecastWeather } from '../../store/forecastWeather';
	import axios from 'axios';

	let newCityName = '';
	let isMounted = false;

	// Current Weather API
	const fetchCurrentWeather = async (city: string) => {
		try {
			const { data } = await axios(
				`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=886f9f7a35e65a64a10bef848d59f3a5&units=metric`
			);
			weatherData.set(data);
			// console.log(data);
		} catch (error) {
			console.error('Error fetching data from fetchCurrentWeather:', error);
			alert('Please Enter Valid City & Pincode');
		}
	};

	// Forecast Data API
	const fetchForecastData = async (city: string) => {
		try {
			const { data } = await axios(
				`https://api.openweathermap.org/data/2.5/forecast?q=${city}&appid=886f9f7a35e65a64a10bef848d59f3a5&units=metric`
			);
			forecastWeather.set(data);
			// console.log(data);
		} catch (error) {
			console.error('Error fetching data from fetchForecastData:', error);
			alert('Please Enter Valid City & Pincode');
		}
	};

	// Fetch weather data
	export const fetchDataFromBothAPIs = async (city: string) => {
		try {
			await Promise.all([fetchCurrentWeather(city), fetchForecastData(city)]);
		} catch (error) {
			console.error('Error fetching data from both APIs:', error);
			alert('Please Enter Valid City & Pincode');
		}
	};

	onMount(() => {
		if (!isMounted) {
			fetchDataFromBothAPIs('Agra'); // Default city name
			isMounted = true;
		}
	});

	function changeCity(event: Event) {
		newCityName = (event.target as HTMLInputElement).value;
		cityName.set(newCityName);
	}

	const handleKeyPress = async (event: KeyboardEvent) => {
		if (event.key === 'Enter') {
			fetchDataFromBothAPIs(newCityName);
		}
	};
</script>

<div class="flex items-center justify-center h-full lg:mt-0 mt-5">
	<label for="citySearch" class="relative">
		<i
			class="fa-solid fa-magnifying-glass text-gray-500 absolute lg:top-3.5 lg:left-3.5 2xl:top-4 2xl:left-5 top-4 left-4"
		></i>
		<input
			class="2xl:py-2 2xl:pl-11 max-lg:px-9 py-2 focus:caret-gray-400 rounded-full appearance-none border-2 border-green-200 focus:outline-none focus:border-green-400 focus:border-opacity-80 text-gray-500 shadow-green-200 shadow-md focus:shadow-none lg:py-1.5 lg:pl-9"
			type="text"
			on:input={changeCity}
			on:keypress={handleKeyPress}
			placeholder="Type City or PIN Code"
			id="citySearch"
		/>
	</label>

	<button
		on:click={() => fetchDataFromBothAPIs($cityName)}
		class="bg-green-300 text-white 2xl:py-2.5 2xl:px-5 lg:px-4 lg:py-2 px-4 py-2 hover:bg-green-400 ml-3 rounded-full shadow-md shadow-green-200"
		><i class="fa-solid fa-arrow-right"></i></button
	>
</div>
