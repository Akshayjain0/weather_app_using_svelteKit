<script lang="ts">
	import { weatherData } from '../../store/weatherStore';
	import cloud from '$lib/assets/cloud-computing.png';
	import sunny from '$lib/assets/sunny.png';
	import rain from '$lib/assets/rainy.png';
	let weather: any;
	let weatherDescription: any = null;
	let icon: any = null;
	weatherData?.subscribe((data) => {
		weather = data;
		weatherDescription = weather?.weather;
		icon = weatherDescription?.[0].icon;
	});

	// Date and Time
	function getFullWeekdayTimeAmPm() {
		const now = new Date();

		const weekday = now.toLocaleDateString('en-US', { weekday: 'long' }); // Full weekday name
		const hours = now.getHours() % 12 || 12; // Get 12-hour format (12 for midnight/noon)
		const minutes = String(now.getMinutes()).padStart(2, '0'); // Add leading zero for single-digit minutes
		const amPm = now.getHours() >= 12 ? 'PM' : 'AM';

		return `${weekday} ${hours}:${minutes} ${amPm}`;
	}

	// Example usage
	const formattedDateTime = getFullWeekdayTimeAmPm();
</script>

<div class="lg:h-full">
	<!--Start Div-1 City_Name, Image, Curr. Temp, Day, Hr Rule -->
	<div class="lg:h-[70%] lg:flex lg:flex-col lg:items-center lg:justify-evenly lg:text-gray-700">
		<div class="2xl:text-6xl 2xl:mb-8 lg:text-5xl lg:font-bold">
			{weather?.name ? weather.name : 'Agra'}
		</div>
		<div class="">
			<img src={`http://openweathermap.org/img/wn/${icon}@4x.png`} alt="" class="" />
		</div>
		<div>
			<h2 class="2xl:text-7xl lg:text-6xl lg:font-semibold 2xl:mt-6">
				{weather?.main?.temp == undefined ? '23.76' : weather?.main?.temp}<sup
					class="2xl:text-5xl lg:text-4xl">&deg;c</sup
				>
			</h2>
		</div>
		<div class="lg:flex lg:flex-col 2xl:mt-4 gap-1 lg:w-full lg:items-center">
			<div class="lg:flex lg:items-center 2xl:w-[50%] lg:w-[60%] lg:justify-start">
				<span><i class="fa-solid fa-circle-dot lg:text-gray-500 lg:text-sm"></i></span>
				<p class="2xl:text-xl lg:text-gray-600 capitalize ml-3">
					{weatherDescription?.[0].main == undefined ? 'Cloudy' : weatherDescription?.[0].main}
				</p>
			</div>
			<div class="lg:flex lg:items-center 2xl:w-[50%] lg:w-[60%] lg:justify-start">
				<span><i class="fa-solid fa-circle-dot lg:text-gray-500 lg:text-sm"></i></span>
				<p class="2xl:text-xl lg:text-gray-600 capitalize ml-3">
					{weatherDescription?.[0].description == undefined
						? 'Clear Sky'
						: weatherDescription?.[0].description}
				</p>
			</div>
		</div>
		<div class="lg:w-[80%]">
			<hr class="lg:h-0.5 2xl:my-8 lg:bg-gray-200 lg:border-1 lg:dark:bg-gray-400" />
		</div>
	</div>
	<!--End Div-1 City_Name, Image, Curr. Temp, Day, Hr Rule-->

	<!-- Start Div-2 Cloud Detail, Rain Detail, Temp Min, Temp Max -->

	<div class="lg:h-[30%] lg:flex lg:flex-col lg:items-start lg:ml-12 lg:text-gray-500">
		<div class="2xl:mb-5">
			<p class="2xl:text-2xl lg:text-xl lg:text-gray-600">
				{formattedDateTime}
			</p>
		</div>
		<div class="lg:flex lg:flex-col 2xl:mb-5 gap-2">
			<div class="2xl:text-lg lg:text-md lg:flex lg:font-medium">
				<span>
					<i class="fa-solid fa-cloud-sun lg:mr-5 lg:text-gray-700"></i>
				</span>
				Cloudy {weather?.clouds.all == undefined ? '66' : weather?.clouds.all}%
			</div>
			<div class="2xl:text-lg lg:text-md lg:flex lg:font-medium " >
				<span>
					<i class="fa-solid fa-temperature-low lg:mr-6 lg:text-gray-700"></i>
				</span>
				Feels like - {weather?.main?.feels_like == undefined
					? '22.56'
					: weather?.main?.feels_like}&deg;c
			</div>
			<div class="2xl:text-lg lg:text-md lg:flex lg:font-medium">
				<span>
					<i class="fa-solid fa-arrow-up-from-ground-water lg:mr-5 lg:text-gray-700"></i>
				</span>
				{weather?.main?.pressure == undefined ? '1011' : weather?.main?.pressure} hPa
			</div>
		</div>

		<div class="lg:flex lg:justify-start lg:w-[80%] 2xl:gap-x-10 lg:gap-x-6">
			<div class="2xl:text-2xl lg:text-lg">
				<span><i class="fa-solid fa-temperature-arrow-up"></i></span>
				<span
					>{weather?.main?.temp_min == undefined ? '21.43' : weather?.main?.temp_min}<sup
						class="lg:text-xs lg:font-semibold">&#8451;</sup
					></span
				>
			</div>
			<div class="2xl:text-2xl lg:text-lg">
				<span><i class="fa-solid fa-temperature-arrow-down"></i></span>
				<span
					>{weather?.main?.temp_max == undefined ? '22.55' : weather?.main?.temp_max}<sup
						class="lg:text-xs lg:font-semibold">&#8451;</sup
					></span
				>
			</div>
		</div>
	</div>
	<!-- End Div-2 Cloud Detail, Rain Detail, Temp Min, Temp Max -->
</div>
