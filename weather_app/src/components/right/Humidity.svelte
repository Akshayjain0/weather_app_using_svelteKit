<script lang="ts">
	import humidity from '$lib/assets/humidity.png';
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
		<p class="text-gray-400 lg:text-xl sm:text-2xl text-xl">Humidity</p>
	</div>
	<div class="flex justify-between w-[90%] items-center">
		<p class="2xltext-6xl lg:text-5xl font-normal sm:text-3xl text-2xl">
			{weather?.main.humidity == undefined ? '5' : weather?.main.humidity}<sup class="lg:text-2xl"
				>%</sup
			>
		</p>
	</div>
	<div>
		<img
			src={humidity}
			class="2xl:w-10 2xl:h-10 lg:w-10 lg:h-10 sm:w-12 sm:h-12 w-8 h-8 lg:text-green-400"
			alt=""
		/>
	</div>
</div>
