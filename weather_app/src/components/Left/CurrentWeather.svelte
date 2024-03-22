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

<div
	class="lg:h-full max-lg:flex max-lg:flex-row md:justify-evenly max-sm:justify-between lg:mb-0 mb-5"
>
	<!--Start Div-1 City_Name, Image, Curr. Temp, Day, Hr Rule -->
	<div class="lg:h-[70%] flex flex-col items-center justify-evenly text-gray-700 lg:mt-0 mt-5">
		<div
			class="2xl:text-6xl 2xl:mb-8 lg:text-5xl text-3xl max-lg:mb-3 font-bold md:max-lg:text-6xl"
		>
			{weather?.name ? weather.name : 'Agra'}
		</div>
		<div class="">
			<img src={`http://openweathermap.org/img/wn/${icon}@4x.png`} alt="" class="" />
		</div>
		<div>
			<h2 class="2xl:text-7xl lg:text-6xl font-semibold 2xl:mt-6 text-3xl">
				{weather?.main?.temp == undefined ? '23.76' : weather?.main?.temp}<sup
					class="2xl:text-5xl lg:text-4xl">&deg;c</sup
				>
			</h2>
		</div>
		<div class="flex flex-col 2xl:mt-4 gap-1 lg:w-full lg:items-center lg:mt-0 mt-3 max-lg:hidden">
			<div class="flex items-center 2xl:w-[50%] lg:w-[60%] justify-start">
				<span
					><i class="fa-solid fa-circle-dot lg:text-gray-500 lg:text-sm lg:block max-lg:hidden"
					></i></span
				>
				<p class="2xl:text-xl lg:text-gray-600 capitalize ml-3">
					{weatherDescription?.[0].main == undefined ? 'Cloudy' : weatherDescription?.[0].main}
				</p>
			</div>
			<div class="lg:flex lg:items-center 2xl:w-[50%] lg:w-[60%] lg:justify-start">
				<span
					><i class="fa-solid fa-circle-dot lg:text-gray-500 lg:text-sm lg:block max-lg:hidden"
					></i></span
				>
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

	<div
		class="lg:h-[30%] lg:flex lg:flex-col lg:items-start lg:ml-12 text-gray-500 lg:mt-0 mt-5 max-sm:text-lg md:text-xl lg:text-base max-sm:mr-1.5"
	>
		<div class="2xl:mb-5 max-lg:text-gray-700 md:max-lg:mt-2">
			<p class="2xl:text-2xl lg:text-2xl lg:text-gray-600 text-2xl mr-3 md:max-lg:text-4xl">
				{formattedDateTime}
			</p>
		</div>
		<div class="flex flex-col 2xl:mb-5 gap-2 max-lg:gap-5 max-sm:mt-3 2xl-mt-0 xl:mt-4 max-lg:mt-6">
			<div class="2xl:text-lg lg:text-md lg:flex lg:font-medium">
				<span>
					<i class="fa-solid fa-cloud-sun lg:mr-5 lg:text-gray-700"></i>
				</span>
				Cloudy {weather?.clouds.all == undefined ? '66' : weather?.clouds.all}%
			</div>
			<div class="2xl:text-lg lg:text-md lg:flex lg:font-medium">
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

		<div
			class="flex justify-start lg:w-[80%] 2xl:gap-x-10 lg:gap-x-6 max-2xl:mt-3 max-lg:gap-5 max-lg:mt-6"
		>
			<div class="2xl:text-2xl lg:text-lg">
				<span><i class="fa-solid fa-temperature-arrow-up text-red-400"></i></span>
				<span
					>{weather?.main?.temp_min == undefined ? '21.43' : weather?.main?.temp_min}<sup
						class="lg:text-xs lg:font-semibold">&#8451;</sup
					></span
				>
			</div>
			<div class="2xl:text-2xl lg:text-lg">
				<span><i class="fa-solid fa-temperature-arrow-down text-blue-400"></i></span>
				<span
					>{weather?.main?.temp_max == undefined ? '22.55' : weather?.main?.temp_max}<sup
						class="lg:text-xs lg:font-semibold">&#8451;</sup
					></span
				>
			</div>
		</div>
		<div class="flex max-sm:text-base justify-start mt-3 lg:hidden">
			<p class="mr-5">
				{weatherDescription?.[0].main == undefined ? 'Cloudy' : weatherDescription?.[0].main}
			</p>

			<p class="">
				{weatherDescription?.[0].description == undefined
					? 'Clear Sky'
					: weatherDescription?.[0].description}
			</p>
		</div>
	</div>
	<!-- End Div-2 Cloud Detail, Rain Detail, Temp Min, Temp Max -->
</div>
