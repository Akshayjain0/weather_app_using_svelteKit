<script>
	import CurrentWeather from './CurrentWeather.svelte';
	import CitySearch from './CitySearch.svelte';
</script>

<div class="flex flex-col w-full h-screen">
	<div class="h-[15%]"><CitySearch /></div>
	<div class="h-[85%]"><CurrentWeather /></div>
</div>
