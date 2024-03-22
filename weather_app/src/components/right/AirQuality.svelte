<script lang="ts">
	import airQuality from '$lib/assets/wind.png';
	import { weatherData } from '../../store/weatherStore';
	let weather: any;
	weatherData?.subscribe((data) => {
		weather = data;
	});
</script>

<div
	class="2xl:w-80 2xl:h-64 lg:w-56 lg:h-52 h-48 w-44 sm:h-60 sm:w-56 bg-white shadow-md rounded-3xl flex flex-col items-start justify-between 2xl:px-10 2xl:py-8 lg:px-8 lg:py-5 sm:px-5 sm:py-6 px-5 py-4"
>
	<div>
		<p class="text-gray-400 lg:text-xl sm:text-2xl text-xl">More</p>
	</div>
	<div class="flex items-center">
		<span>
			<i
				class="fa-solid fa-arrow-up-from-ground-water lg:mr-5 sm:mr-5 text-green-500 lg:text-xl sm:text-3xl text-xl mr-3"
			></i>
		</span>
		<p class="2xl:text-xl lg:text-base sm:text-xl text-base">
			Pressure - <span class="text-gray-500"
				>{weather?.main?.pressure == undefined ? '1011' : weather?.main?.pressure} hPa</span
			>
		</p>
	</div>
	<div class="flex items-center">
		<i
			class="fa-solid fa-temperature-low lg:mr-6 sm:mr-5 text-green-500 lg:text-2xl sm:text-3xl text-xl mr-3"
		></i>
		<p class="2xl:text-xl lg:text-base sm:text-xl text-base">
			Feels Like <span class="text-gray-500"
				>{weather?.main?.feels_like == undefined ? '22.56' : weather?.main?.feels_like} &deg;c</span
			>
		</p>
	</div>
</div>
