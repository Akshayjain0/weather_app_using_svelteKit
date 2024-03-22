<script>
	import DaysForecast from './DaysForecast.svelte';
	import TodaysHighlights from './TodaysHighlights.svelte';
</script>

<div class="flex flex-col w-full lg:h-screen">
	<div class="lg:w-full lg:h-[30%]"><DaysForecast /></div>
	<div class="lg:w-full lg:h-[70%]"><TodaysHighlights /></div>
</div>
