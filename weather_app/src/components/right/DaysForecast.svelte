<script>
	import sun from '$lib/assets/sun.png';
</script>

<div class="h-full lg:flex lg:flex-col lg:justify-evenly lg:mx-28">
	<div>
		<h1 class="text-3xl text-gray-800 font-semibold">7-Days Weather Forecast</h1>
	</div>
	<div class="lg:grid lg:grid-flow-col">
		<div
			class="bg-white w-36 h-44 lg:flex lg:flex-col lg:items-center lg:rounded-2xl lg:justify-evenly lg:shadow-md"
		>
			<div class="font-medium text-lg uppercase">Sun</div>
			<div class="lg:w-16 lg:h-16">
				<img src={sun} alt="weather" />
			</div>
			<div class="font-semibold">
				<span>
					20<sup class="text-sm font-semibold">&deg;</sup>
				</span>-
				<span class="text-gray-500">
					18<sup class="text-sm">&deg;</sup>
				</span>
			</div>
		</div>

		<div
			class="bg-white w-36 h-44 lg:flex lg:flex-col lg:items-center lg:rounded-2xl lg:justify-evenly lg:shadow-md"
		>
			<div class="font-medium text-lg uppercase">Mon</div>
			<div class="lg:w-16 lg:h-16">
				<img src={sun} alt="weather" />
			</div>
			<div>
				<span>
					22<sup class="text-sm font-semibold">&deg;</sup>
				</span>-
				<span class="text-gray-500">
					10<sup class="text-sm font-semibold">&deg;</sup>
				</span>
			</div>
		</div>

		<div
			class="bg-white w-36 h-44 lg:flex lg:flex-col lg:items-center lg:rounded-2xl lg:justify-evenly lg:shadow-md"
		>
			<div class="font-medium text-lg uppercase">Tue</div>
			<div class="lg:w-16 lg:h-16">
				<img src={sun} alt="weather" />
			</div>
			<div>
				<span>
					15<sup class="text-sm font-semibold">&deg;</sup>
				</span>-
				<span class="text-gray-500">
					18<sup class="text-sm font-semibold">&deg;</sup>
				</span>
			</div>
		</div>

		<div
			class="bg-white w-36 h-44 lg:flex lg:flex-col lg:items-center lg:rounded-2xl lg:justify-evenly lg:shadow-md"
		>
			<div class="font-medium text-lg uppercase">Wed</div>
			<div class="lg:w-16 lg:h-16">
				<img src={sun} alt="weather" />
			</div>
			<div>
				<span>
					20<sup class="text-sm font-semibold">&deg;</sup>
				</span>-
				<span class="text-gray-500">
					18<sup class="text-sm font-semibold">&deg;</sup>
				</span>
			</div>
		</div>

		<div
			class="bg-white w-36 h-44 lg:flex lg:flex-col lg:items-center lg:rounded-2xl lg:justify-evenly lg:shadow-md"
		>
			<div class="font-medium text-lg uppercase">Thu</div>
			<div class="lg:w-16 lg:h-16">
				<img src={sun} alt="weather" />
			</div>
			<div>
				<span>
					22<sup class="text-sm font-semibold">&deg;</sup>
				</span>-
				<span class="text-gray-500">
					18<sup class="text-sm font-semibold">&deg;</sup>
				</span>
			</div>
		</div>

		<div
			class="bg-white w-36 h-44 lg:flex lg:flex-col lg:items-center lg:rounded-2xl lg:justify-evenly lg:shadow-md"
		>
			<div class="font-medium text-lg uppercase">Fri</div>
			<div class="lg:w-16 lg:h-16">
				<img src={sun} alt="weather" />
			</div>
			<div>
				<span>
					20<sup class="text-sm font-semibold">&deg;</sup>
				</span>-
				<span class="text-gray-500">
					18<sup class="text-sm font-semibold">&deg;</sup>
				</span>
			</div>
		</div>

		<div
			class="bg-white w-36 h-44 lg:flex lg:flex-col lg:items-center lg:rounded-2xl lg:justify-evenly lg:shadow-md"
		>
			<div class="font-medium text-lg uppercase">Sat</div>
			<div class="lg:w-16 lg:h-16">
				<img src={sun} alt="weather" />
			</div>
			<div>
				<span>
					21<sup class="text-sm font-semibold">&deg;</sup>
				</span>-
				<span class="text-gray-500">
					22<sup class="text-sm font-semibold">&deg;</sup>
				</span>
			</div>
		</div>
	</div>
</div>
