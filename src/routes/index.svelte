<script>
	import WeatherDetail from '../components/weather_detail.svelte';

	let city = '';
	let arrayWeather = '';
	function handleInput(event) {
		city = event.target.value;
	}
	async function fetchData() {
		const response = await fetch(
			`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=630cde63b6f9f0dae6abcca158c8a36b`
		);
		city='';
		const data = await response.json();
		arrayWeather = data;
	}
</script>

<main>
	<input type="text" value={city} on:input={handleInput} />
	<button on:click={() => fetchData()}>search</button>
	{#await arrayWeather}
		<p>cargando...</p>
	{:then weather}
		{#if weather != ''}
			<WeatherDetail {arrayWeather} />
		{:else}
			<div />
		{/if}
	{/await}
</main>

<style>
	/* your styles go here */
	input[type='text'] ,input[type=text]:not(.browser-default):focus:not([readonly]){
		margin: 5px;
		padding: 0px 10px;
		width: 90%;
		border-radius: 15px;
		border: 3px solid #39c;
		-webkit-box-shadow: none;
		box-shadow: none;
	}
</style>
