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
				temp: forecast?.main?.temp.toFixed(1),
				feels_like: forecast?.main?.feels_like.toFixed(1),
				weather_description: forecast?.weather?.[0]?.description,
				icon: forecast?.weather?.[0]?.icon === undefined ? "10d": forecast?.weather?.[0]?.icon
			});
		}
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

<div
	class="lg:h-full flex flex-col max-lg:justify-evenly 2xl:mx-28 lg:mx-14 mx-6 md:mx-12 md:mt-8 mt-3"
>
	<div class="lg:mb-5 md:mb-12 mb-4">
		<h1 class="2xl:text-3xl lg:text-2xl md:text-4xl text-xl text-gray-800 font-semibold">
			5-Days Weather Forecast
		</h1>
	</div>
	<div
		class="grid grid-flow-col 2xl:gap-x-0 lg:gap-x-2 max-sm:gap-x-2 max-sm:gap-y-5 lg:gap-y-0 md:gap-y-6 max-lg:grid-rows-2 max-sm:mt-6 max-sm:justify-items-center md:justify-items-center"
	>
		{#each nextFiveDaysData as day, index}
			<div
				class="bg-white 2xl:w-36 2xl:h-44 lg:w-28 lg:h-36 md:w-52 md:h-60 h-44 w-28 flex flex-col items-center rounded-2xl justify-evenly shadow-md max-lg:py-2"
			>
				<div
					class="lg:font-medium 2xl:text-lg lg:text-base uppercase md:text-2xl font-medium text-base"
				>
					{day.day == undefined ? 'SUNDAYS' : day.day}
				</div>
				<div class="2xl:w-16 2xl:h-16 lg:w-12 lg:h-12 md:w-32">
					<img src={`http://openweathermap.org/img/wn/${day.icon}@4x.png`} alt="weather" />
				</div>
				<div class="font-semibold max-lg:text-xl max-sm:text-base">
					<span>
						{day.temp == undefined ? '19' : day.temp}<sup
							class="2xl:text-sm lg:text-xs lg:font-semibold">&deg;</sup
						>
					</span>-
					<span class="text-gray-500">
						{day.feels_like == undefined ? 20 : day.feels_like}<sup class="2xl:text-sm lg:text-xs"
							>&deg;</sup
						>
					</span>
				</div>
			</div>
		{/each}
	</div>
</div>
