<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	import { weatherData } from '../../store/weatherStore';
	import axios from 'axios';

	const dispatch = createEventDispatcher();
	let inputText = '';
	const handleInput = (event: Event) => {
		let target = event.target as HTMLInputElement;
		inputText = target.value;
	};

	const handleKeyPress = async (event: KeyboardEvent) => {
		if (event.key === 'Enter') {
			weatherData.set('Set WET HELlo');
		}
	};

	const handleClick = async () => {
		try {
			// const response = await axios.get(
			// 	`https://api.openweathermap.org/data/2.5/weather?q=${inputText}&appid=YOUR_API_KEY`
			// );
			weatherData.set('Set WET HELlo');
			// console.log(inputText)
		} catch (error) {
			console.error('Error While Fetching Data:->>', error);
		}
	};
</script>

<div class="lg:flex lg:items-center lg:justify-center lg:mt-10">
	<label for="citySearch" class="relative">
		<i class="fa-solid fa-magnifying-glass text-gray-400 absolute top-4 left-3.5"></i>
		<input
			class="w-full py-2.5 focus:caret-gray-400 pl-9 appearance-none border-2 border-green-200 rounded-full focus:outline-none focus:bg-white focus:border-green-400 focus:border-opacity-80 text-gray-600 shadow-green-200 shadow-md focus:shadow-none"
			type="text"
			bind:value={inputText}
			on:keypress={handleKeyPress}
			on:input={handleInput}
			placeholder="Type city..."
			id="citySearch"
		/>
	</label>

	<button
		on:click={handleClick}
		class="bg-transparen hover:border-transparent bg-green-300 text-white py-2.5 px-5 hover:bg-green-400 ml-3 rounded-full shadow-md shadow-green-200"
		><i class="fa-solid fa-arrow-right"></i></button
	>
</div>
