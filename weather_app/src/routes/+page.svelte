<script>
	import LeftSection from '../components/Left/LeftSection.svelte';
	import RightSection from '../components/right/RightSection.svelte';
</script>

<main>
	<div class="lg:w-full lg:h-screen lg:flex lg:flex-row flex flex-col w-full">
		<div class="lg:w-[25%] lg:h-screen">
			<LeftSection />
		</div>
		<div class="lg:w-[75%] lg:h-screen bg-[#f6f6f8]">
			<RightSection />
		</div>
	</div>
</main>
