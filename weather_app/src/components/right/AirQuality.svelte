<script>
	import airQuality from '$lib/assets/wind.png';
</script>

<div
	class="w-80 h-64 bg-white shadow-md rounded-3xl flex flex-col items-start justify-between px-10 py-8"
>
	<div>
		<p class="text-gray-400 text-xl">Humidity</p>
	</div>
	<div class="flex justify-between w-[90%]">
		<p class="text-6xl">12<sup class="text-4xl">%</sup></p>
		<img src={airQuality} class="w-16 h-16 text-green-400" alt="" />
	</div>
	<div>
		<p class="text-xl">Unhealthy 👎</p>
	</div>
</div>
