<script>
	import AirQuality from './AirQuality.svelte';
	import Humidity from './Humidity.svelte';
	import SunriseSunset from './Sunrise_Sunset.svelte';
	import UvIndex from './UvIndex.svelte';
	import Visibility from './Visibility.svelte';
	import WIndSpeed from './WIndSpeed.svelte';
</script>

<div class="lg:flex lg:flex-col lg:justify-evenly 2xl:mx-28 lg:mx-14 lg:mt-5 lg:gap-0">
	<div>
		<h2 class="lg:text-gray-800 2xl:text-3xl lg:text-2xl font-semibold">Today's Highlights</h2>
	</div>
	<div class="lg:grid lg:grid-flow-row lg:grid-cols-3 2xl:gap-5 lg:gap-4 2xl:mt-10 lg:mt-5">
		<UvIndex />
		<WIndSpeed />
		<SunriseSunset />
		<Humidity />
		<Visibility />
		<AirQuality />
	</div>
</div>
