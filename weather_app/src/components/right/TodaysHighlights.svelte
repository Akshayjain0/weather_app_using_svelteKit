<script>
	import AirQuality from './AirQuality.svelte';
	import Humidity from './Humidity.svelte';
	import SunriseSunset from './Sunrise_Sunset.svelte';
	import UvIndex from './UvIndex.svelte';
	import Visibility from './Visibility.svelte';
	import WIndSpeed from './WIndSpeed.svelte';
</script>

<div
	class="flex flex-col justify-evenly 2xl:mx-28 lg:mx-14 lg:mt-5 lg:gap-0 sm:mt-12 mt-9 sm:mx-4 max-sm:mx-2 sm:mb-6 max-sm:mb-6"
>
	<div>
		<h2
			class="lg:text-gray-800 2xl:text-3xl lg:text-2xl font-semibold sm:text-4xl text-xl max-lg:ml-8 max-sm:ml-4 max-sm:mb-6"
		>
			Today's Highlights
		</h2>
	</div>
	<div
		class="grid lg:grid-flow-row lg:grid-cols-3 md:grid-cols-3 grid-cols-2 gap-y-7 justify-items-center 2xl:gap-5 lg:gap-4 2xl:mt-10 lg:mt-5 sm:mt-10 sm:gap-y-8"
	>
		<UvIndex />
		<WIndSpeed />
		<SunriseSunset />
		<Humidity />
		<Visibility />
		<AirQuality />
	</div>
</div>
