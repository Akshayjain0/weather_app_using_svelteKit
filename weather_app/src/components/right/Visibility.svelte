<script lang="ts">
	import { weatherData } from '../../store/weatherStore';

	let weather: any;
	weatherData?.subscribe((data) => {
		weather = data;
	});


</script>

<div
	class="2xl:w-80 2xl:h-64 lg:w-56 lg:h-52 lg:bg-white lg:shadow-md lg:rounded-3xl lg:flex lg:flex-col lg:items-start lg:justify-between 2xl:px-10 2xl:py-8 lg:px-8 lg:py-5"
>
	<div><p class="lg:text-gray-400 lg:text-xl">Visibility</p></div>
	<div>
		<p class="2xltext-6xl lg:text-5xl lg:font-normal">
			{weather?.visibility == undefined ? '10' : weather?.visibility / 1000}<span
				class="2xl:text-2xl lg:text-xl">km/h</span
			>
		</p>
	</div>
	<div class="lg:text-2xl lg:text-green-500"><i class="fa-regular fa-eye"></i></div>
</div>
