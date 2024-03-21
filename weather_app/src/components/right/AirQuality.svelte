<script lang="ts">
	import airQuality from '$lib/assets/wind.png';
	import { weatherData } from '../../store/weatherStore';
	let weather: any;
	weatherData?.subscribe((data) => {
		weather = data;
	});
</script>

<div
	class="2xl:w-80 2xl:h-64 lg:w-56 lg:h-52 lg:bg-white lg:shadow-md lg:rounded-3xl lg:flex lg:flex-col lg:items-start lg:justify-between 2xl:px-10 2xl:py-8 lg:px-8 lg:py-5"
>
	<div>
		<p class="lg:text-gray-400 lg:text-xl">More</p>
	</div>
	<div class="lg:flex lg:items-center">
		<span>
			<i class="fa-solid fa-arrow-up-from-ground-water lg:mr-5 lg:text-green-500 lg:text-xl"></i>
		</span>
		<p class="2xl:text-xl">
			Pressure - {weather?.main?.pressure == undefined ? '1011' : weather?.main?.pressure} hPa
		</p>
	</div>
	<div class="lg:flex lg:items-center">
		<i class="fa-solid fa-temperature-low lg:mr-6 lg:text-green-500 lg:text-2xl"></i>
		<p class="2xl:text-xl">
			<span>Feels</span> Like {weather?.main?.feels_like == undefined
				? '22.56'
				: weather?.main?.feels_like} &deg;c
		</p>
	</div>
</div>
