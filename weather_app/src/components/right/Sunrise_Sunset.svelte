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
	class="2xl:w-80 2xl:h-64 lg:w-56 lg:h-52 h-48 w-44 sm:h-60 sm:w-56 bg-white shadow-md rounded-3xl flex flex-col items-start justify-between 2xl:px-10 2xl:py-8 lg:px-8 lg:py-5 sm:px-5 sm:py-6 px-5 py-4"
>
	<div>
		<p class="text-gray-400 lg:text-xl sm:text-2xl text-lg">Sunrise & Sunset</p>
	</div>
	<div class="2xl:w-[60%] lg:w-[80%] sm:w-[70%] w-[80%] flex justify-between">
		<div>
			<i class="fa-regular fa-circle-up text-green-400 2xl:text-4xl lg:text-3xl sm:text-3xl text-xl"
			></i>
		</div>
		<div>
			<div class="md:font-semibold sm:text-xl text-lg">
				{weather?.sys.sunrise == undefined ? '6:25 AM' : convertUnixToHourMin(weather?.sys.sunrise)}
			</div>
		</div>
	</div>
	<div class="2xl:w-[60%] lg:w-[80%] sm:w-[70%] w-[80%] flex justify-between">
		<div>
			<i
				class="fa-regular fa-circle-down text-green-400 2xl:text-4xl lg:text-3xl sm:text-3xl text-xl"
			></i>
		</div>
		<div>
			<div class="md:font-semibold sm:text-xl text-lg">
				{weather?.sys.sunrise == undefined ? '6:25 AM' : convertUnixToHourMin(weather?.sys.sunset)}
			</div>
		</div>
	</div>
</div>
