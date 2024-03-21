<script lang="ts">
	import sun from '$lib/assets/sun.png';
	import { onMount, onDestroy } from 'svelte';
	import { forecastWeather } from '../../store/forecastWeather';

	let forecastData: any;
	const nextFiveDaysData: ForecastItem[] = [];
	const daysOfWeek = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];

	// Subscribe to forecastWeather changes
	forecastWeather.subscribe((data) => {
		forecastData = data;
		extractNextFiveDaysData(); // Call the function when forecastData changes
	});

	// Function to extract data for the next five days
	function extractNextFiveDaysData() {
		nextFiveDaysData.length = 0; // Clear the array
		for (let i = 1; i <= 5; i++) {
			const dayIndex = i * 7;
			const forecast = forecastData?.list?.[dayIndex];
			const date = new Date(forecast?.dt * 1000); // Convert timestamp to date

			nextFiveDaysData.push({
				day: daysOfWeek[date.getDay()],
				temp: forecast?.main?.temp,
				feels_like: forecast?.main?.feels_like,
				weather_description: forecast?.weather?.[0]?.description,
				icon: forecast?.weather?.[0]?.icon
			});
		}
		console.log(nextFiveDaysData);
	}

	// Run the function on component mount
	onMount(() => {
		extractNextFiveDaysData();
	});

	// onDestroy(() => {
	//     // Clean up subscriptions
	//     forecastWeather.unsubscribe();
	// });

	interface ForecastItem {
		day: string;
		temp?: number;
		feels_like?: number;
		weather_description?: string;
		icon?: string;
	}
</script>

<div class="lg:h-full lg:flex lg:flex-col lg:justify-evenly 2xl:mx-28 lg:mx-14">
	<div>
		<h1 class="2xl:text-3xl lg:text-2xl lg:text-gray-800 lg:font-semibold">
			5-Days Weather Forecast
		</h1>
	</div>
	<div class="lg:grid lg:grid-flow-col 2xl:gap-x-0 lg:gap-x-2">
		{#each nextFiveDaysData as day, index}
			<div
				class="lg:bg-white 2xl:w-36 2xl:h-44 lg:w-28 lg:h-36 lg:flex lg:flex-col lg:items-center lg:rounded-2xl lg:justify-evenly lg:shadow-md"
			>
				<div class="lg:font-medium 2xl:text-lg lg:text-base lg:uppercase">{day.day}</div>
				<div class="2xl:w-16 2xl:h-16 lg:w-12 lg:h-12">
					<img src={`http://openweathermap.org/img/wn/${day.icon}@4x.png`} alt="weather" />
				</div>
				<div class="lg:font-semibold">
					<span>
						{day.temp}<sup class="2xl:text-sm lg:text-xs lg:font-semibold">&deg;</sup>
					</span>-
					<span class="lg:text-gray-500">
						{day.feels_like}<sup class="2xl:text-sm lg:text-xs">&deg;</sup>
					</span>
				</div>
			</div>
		{/each}
	</div>
</div>
