<script lang="ts">
	import UvIndex from '$lib/assets/uv-index.png';
	import { weatherData } from '../../store/weatherStore';
	let weather: any;
	weatherData?.subscribe((data) => {
		weather = data;
	});
	let cloudPercentage = weather?.clouds?.all; // Example cloud percentage, you can replace it with your actual value

	// Function to determine UV index range based on cloud percentage
	function getUVIndexRange(cloudPercentage: number) {
		if (cloudPercentage >= 80) {
			return '1-2';
		} else if (cloudPercentage >= 60) {
			return '3-4';
		} else if (cloudPercentage >= 40) {
			return '5-6';
		} else if (cloudPercentage >= 20) {
			return '7-8';
		} else {
			return '9-10';
		}
	}

	// Example function call
	let uvIndexRange = getUVIndexRange(cloudPercentage);

	function getUVIndexMessage(cloudPercentage: number) {
		if (cloudPercentage >= 80) {
			return 'Poor 😓';
		} else if (cloudPercentage >= 60) {
			return 'Average ☹️';
		} else if (cloudPercentage >= 40) {
			return 'Good 👍';
		} else if (cloudPercentage >= 20) {
			return 'Very Good 😄';
		} else {
			return 'Excellent 🎉';
		}
	}

	// Example function call
	let uvIndexMessage = getUVIndexMessage(cloudPercentage);
</script>

<div
	class="2xl:w-80 2xl:h-64 lg:w-56 lg:h-52 lg:bg-white lg:shadow-md lg:rounded-3xl lg:flex lg:flex-col lg:items-start lg:justify-between 2xl:px-10 2xl:py-8 lg:px-8 lg:py-5"
>
	<div>
		<p class="lg:text-gray-400 lg:text-xl">UV Index</p>
	</div>
	<div class="lg:flex lg:justify-between lg:w-[90%] lg:items-center">
		<p class="2xltext-6xl lg:text-5xl lg:font-normal">
			{uvIndexRange}<sup class="lg:text-2xl"></sup>
		</p>
		<img src={UvIndex} class="2xl:w-16 2xl:h-16 lg:w-10 lg:h-10 lg:text-green-400" alt="" />
	</div>
	<div>
		<p class="lg:text-xl">{uvIndexMessage}</p>
	</div>
</div>
