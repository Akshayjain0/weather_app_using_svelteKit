<script lang="ts">
	import { weatherData } from '../../store/weatherStore';

	let weather: any;
	weatherData?.subscribe((data) => {
		weather = data;
	});
</script>

<div
	class="2xl:w-80 2xl:h-64 lg:w-56 lg:h-52 h-48 w-44 sm:h-60 sm:w-56 bg-white shadow-md rounded-3xl flex flex-col items-start justify-between 2xl:px-10 2xl:py-8 lg:px-8 lg:py-5 sm:px-5 sm:py-6 px-5 py-4"
>
	<div><p class="text-gray-400 lg:text-xl sm:text-2xl text-xl">Visibility</p></div>
	<div>
		<p class="2xltext-6xl lg:text-5xl lg:font-normal sm:text-3xl text-2xl">
			{weather?.visibility == undefined ? '10' : weather?.visibility / 1000}<span
				class="2xl:text-2xl lg:text-xl sm:text-xl">km/h</span
			>
		</p>
	</div>
	<div class="lg:text-2xl text-green-500 sm:text-2xl text-xl">
		<i class="fa-regular fa-eye"></i>
	</div>
</div>
