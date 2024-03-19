<script>
	import AirQuality from './AirQuality.svelte';
	import Humidity from './Humidity.svelte';
	import SunriseSunset from './Sunrise_Sunset.svelte';
	import UvIndex from './UvIndex.svelte';
	import Visibility from './Visibility.svelte';
	import WIndSpeed from './WIndSpeed.svelte';
</script>

<div class="lg:flex lg:flex-col lg:justify-evenly lg:mx-28 lg:mt-5">
	<div>
		<h2 class="text-gray-800 text-3xl font-semibold">Today's Highlights</h2>
	</div>
	<div class="lg:grid lg:grid-flow-row lg:grid-cols-3 gap-5 lg:mt-10">
		<UvIndex />
		<WIndSpeed />
		<SunriseSunset />
		<Humidity />
		<Visibility />
		<AirQuality />
	</div>
</div>
