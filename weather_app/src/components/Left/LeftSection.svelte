<script>
	import CurrentWeather from './CurrentWeather.svelte';
	import CitySearch from './CitySearch.svelte';
</script>

<div class="lg:flex lg:flex-col lg:w-full lg:h-screen ">
	<div class="lg:h-[15%]"><CitySearch /></div>
	<div class="lg:h-[85%]"><CurrentWeather /></div>
</div>
