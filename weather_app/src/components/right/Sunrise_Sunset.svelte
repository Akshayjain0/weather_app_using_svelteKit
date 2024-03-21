<script lang="ts">
	import { weatherData } from '../../store/weatherStore';
	let weather: any;
	weatherData?.subscribe((data) => {
		weather = data;
	});

	function convertUnixToHourMin(timestamp: any) {
		const date = new Date(timestamp * 1000); // Convert UNIX timestamp to milliseconds
		let hours = date.getHours();
		const minutes = date.getMinutes();
		const period = hours < 12 ? 'AM' : 'PM';
		hours = hours % 12 || 12; // Convert 24-hour format to 12-hour format

		return `${hours}:${minutes < 10 ? '0' : ''}${minutes} ${period}`;
	}
</script>

<div
	class="2xl:w-80 2xl:h-64 lg:w-56 lg:h-52 lg:bg-white lg:shadow-md lg:rounded-3xl lg:flex lg:flex-col lg:items-start lg:justify-between 2xl:px-10 2xl:py-8 lg:px-8 lg:py-5"
>
	<div>
		<p class="lg:text-gray-400 lg:text-xl">Sunrise & Sunset</p>
	</div>
	<div class="2xl:w-[50%] lg:w-[70%] lg:flex lg:justify-between lg:items-center">
		<div><i class="fa-regular fa-circle-up lg:text-green-400 2xl:text-4xl lg:text-3xl"></i></div>
		<div>
			<div>
				{weather?.sys.sunrise == undefined ? '6:25 AM' : convertUnixToHourMin(weather?.sys.sunrise)}
			</div>
		</div>
	</div>
	<div class="2xl:w-[50%] lg:w-[70%] lg:flex lg:justify-between lg:items-center">
		<div><i class="fa-regular fa-circle-down lg:text-green-400 2xl:text-4xl lg:text-3xl"></i></div>
		<div>
			<div>
				{weather?.sys.sunrise == undefined ? '6:25 AM' : convertUnixToHourMin(weather?.sys.sunset)}
			</div>
		</div>
	</div>
</div>
