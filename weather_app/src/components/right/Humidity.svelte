<script lang="ts">
	import humidity from '$lib/assets/humidity.png';
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
		<p class="lg:text-gray-400 lg:text-xl">Humidity</p>
	</div>
	<div class="lg:flex lg:justify-between lg:w-[90%] lg:items-center">
		<p class="2xltext-6xl lg:text-5xl lg:font-normal">
			{weather?.main.humidity == undefined ? '5': weather?.main.humidity}<sup class="lg:text-2xl">%</sup>
		</p>
	</div>
	<div>
		<img src={humidity} class="2xl:w-10 2xl:h-10 lg:w-10 lg:h-10 lg:text-green-400" alt="" />
	</div>
</div>
