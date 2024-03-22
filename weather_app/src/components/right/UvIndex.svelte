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
			return 'Excellent 🎉';
		} else if (cloudPercentage >= 60) {
			return 'Very Good 😄';
		} else if (cloudPercentage >= 40) {
			return 'Good 👍';
		} else if (cloudPercentage >= 20) {
			return 'Average ☹️';
		} else {
			return 'Poor 😓';
		}
	}

	// Example function call
	let uvIndexMessage = getUVIndexMessage(cloudPercentage);
</script>

<div
	class="2xl:w-80 2xl:h-64 lg:w-56 lg:h-52 h-48 w-44 sm:h-60 sm:w-56 bg-white shadow-md rounded-3xl flex flex-col items-start justify-between 2xl:px-10 2xl:py-8 lg:px-8 lg:py-5 sm:px-5 sm:py-6 px-5 py-4"
>
	<div>
		<p class="text-gray-400 lg:text-xl sm:text-2xl text-xl">UV Index</p>
	</div>
	<div class="flex justify-between w-full items-center">
		<p class="lg:text-5xl lg:font-normal sm:text-3xl text-2xl">
			{uvIndexRange}
		</p>
		<img
			src={UvIndex}
			class="2xl:w-16 2xl:h-16 lg:w-10 lg:h-10 sm:w-20 sm:h-20 w-14 h-14 lg:text-green-400"
			alt=""
		/>
	</div>
	<div>
		<p class="lg:text-xl sm:text-2xl text-lg">{uvIndexMessage}</p>
	</div>
</div>
