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
				`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=API_KEY&units=metric`
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
				`https://api.openweathermap.org/data/2.5/forecast?q=${city}&appid=API_KEY&units=metric`
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

<div class="lg:flex lg:items-center lg:justify-center lg:h-full">
	<label for="citySearch" class="relative">
		<i
			class="fa-solid fa-magnifying-glass lg:text-gray-500 lg:absolute lg:top-3.5 lg:left-3.5 2xl:top-4 2xl:left-5"
		></i>
		<input
			class="2xl:py-2 2xl:pl-11 lg:focus:caret-gray-400 lg:rounded-full lg:appearance-none lg:border-2 lg:border-green-200 lg:focus:outline-none lg:focus:border-green-400 lg:focus:border-opacity-80 lg:text-gray-500 lg:shadow-green-200 lg:shadow-md lg:focus:shadow-none lg:py-1.5 lg:pl-9"
			type="text"
			on:input={changeCity}
			on:keypress={handleKeyPress}
			placeholder="Type city..."
			id="citySearch"
		/>
	</label>

	<button
		on:click={() => fetchDataFromBothAPIs($cityName)}
		class="lg:bg-green-300 lg:text-white 2xl:py-2.5 2xl:px-5 lg:px-4 lg:py-2 lg:hover:bg-green-400 lg:ml-3 lg:rounded-full lg:shadow-md lg:shadow-green-200"
		><i class="fa-solid fa-arrow-right"></i></button
	>
</div>
