<script lang="ts" type="module">
	import { weatherData } from '../../store/weatherStore';
	import sunny from '$lib/assets/sunny.png';
	let weather: any = '';
	weatherData.subscribe((data) => {
		weather = data;
	});
</script>

<div class="h-full">
	<div class="h-[70%] lg:flex lg:flex-col lg:items-center lg:justify-evenly text-gray-700">
		<div class="text-4xl font-light mb-5">Firozabad</div>
		<div>
			<img src={sunny} alt="" class="lg:w-64 lg:h-64" />
		</div>
		<div>
			<h2 class="lg:text-8xl lg:font-light lg:mt-6">
				12<sup class="text-5xl">&#8451;</sup>
			</h2>
		</div>
		<div>
			<p class="text-3xl mt-5">Monday, <span class="text-gray-400">16:00</span></p>
		</div>
		<div class="lg:w-[80%]">
			<hr class="h-px my-8 bg-gray-200 border-1 dark:bg-gray-400" />
		</div>
	</div>

	<div class="h-[30%] lg:flex lg:flex-col lg:items-start lg:ml-12 lg:gap-10 text-gray-600">
		<div class="text-2xl">
			<span>
				<i class="fa-solid fa-cloud text-2xl text-orange-400"></i>
			</span> Mostly Cloudy
		</div>
		<div class="text-2xl">
			<span>
				<i class="fa-solid fa-cloud-rain text-3xl text-blue-400"></i>
			</span> Rain - 30%
		</div>
		<div class="lg:flex lg:justify-start w-[80%] gap-x-10">
			<div class="text-2xl">
				<span><i class="fa-solid fa-temperature-arrow-up text-red-500"></i></span>
				<span>20<sup class="text-xs font-semibold">&#8451;</sup></span>
			</div>
			<div class="lg:text-2xl">
				<span><i class="fa-solid fa-temperature-arrow-down text-blue-500"></i></span>
				<span>20<sup class="text-xs font-semibold">&#8451;</sup></span>
			</div>
		</div>
	</div>
</div>
