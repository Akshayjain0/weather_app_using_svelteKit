<script>
	import LeftSection from '../components/Left/LeftSection.svelte';
	import RightSection from '../components/right/RightSection.svelte';
</script>

<main>
	<div class="min-w-full min-h-screen flex items-center justify-between">
		<div class="w-[25%] h-screen">
			<LeftSection />
		</div>
		<div class="w-[75%] h-screen bg-gray-50">
			<RightSection />
		</div>
	</div>
</main>
