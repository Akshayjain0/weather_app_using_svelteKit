<script lang="ts">
	import { weatherData } from '../../store/weatherStore';
	let weather: any;
	weatherData?.subscribe((data) => {
		weather = data;
	});

	function getWindDirection(degrees: number) {
		if (degrees >= 337.5 || degrees < 22.5) {
			return 'N';
		} else if (degrees >= 22.5 && degrees < 67.5) {
			return 'NE';
		} else if (degrees >= 67.5 && degrees < 112.5) {
			return 'E';
		} else if (degrees >= 112.5 && degrees < 157.5) {
			return 'SE';
		} else if (degrees >= 157.5 && degrees < 202.5) {
			return 'S';
		} else if (degrees >= 202.5 && degrees < 247.5) {
			return 'SW';
		} else if (degrees >= 247.5 && degrees < 292.5) {
			return 'W';
		} else {
			return 'NW';
		}
	}

	// Example usage
	// const windDegrees = weather?.wind?.deg; // Example wind degrees value
	const windDirection = getWindDirection(
		weather?.wind?.deg == undefined ? '90' : weather?.wind?.deg
	);
</script>

<div
	class="2xl:w-80 2xl:h-64 lg:w-56 lg:h-52 h-48 w-44 sm:h-60 sm:w-56 bg-white shadow-md rounded-3xl flex flex-col items-start justify-between 2xl:px-10 2xl:py-8 lg:px-8 lg:py-5 sm:px-5 sm:py-6 px-5 py-4"
>
	<div><p class="text-gray-400 lg:text-xl sm:text-2xl text-xl">Wind Status</p></div>
	<div>
		<p class="2xltext-6xl lg:text-5xl lg:font-normal sm:text-3xl text-2xl">
			{weather?.wind?.speed == undefined ? 5.6 : weather?.wind?.speed}<span
				class="2xl:text-2xl lg:text-xl sm:text-xl text-lg">km/h</span
			>
		</p>
	</div>
	<div class="lg:text-xl sm:text-2xl text-xl">
		<span class="mr-2"><i class="fa-regular fa-compass text-green-500 text-xl"></i></span>
		{windDirection}
	</div>
</div>
