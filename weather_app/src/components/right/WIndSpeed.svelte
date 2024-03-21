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
	const windDirection = getWindDirection(weather?.wind?.deg == undefined ? "90": weather?.wind?.deg);
</script>

<div
	class="2xl:w-80 2xl:h-64 lg:w-56 lg:h-52 lg:bg-white lg:shadow-md lg:rounded-3xl lg:flex lg:flex-col lg:items-start lg:justify-between 2xl:px-10 2xl:py-8 lg:px-8 lg:py-5"
>
	<div><p class="lg:text-gray-400 lg:text-xl">Wind Status</p></div>
	<div>
		<p class="2xltext-6xl lg:text-5xl lg:font-normal">
			{weather?.wind?.speed == undefined ? 5.6 : weather?.wind?.speed}<span
				class="2xl:text-2xl lg:text-xl">km/h</span
			>
		</p>
	</div>
	<div class="lg:text-xl">
		<span class="lg:mr-2"><i class="fa-regular fa-compass lg:text-green-500"></i></span>
		{windDirection}
	</div>
</div>
