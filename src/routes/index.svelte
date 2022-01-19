<script>
	import WeatherDetail from '../components/weather_detail.svelte';

    let city = '';
    let search=true;
	let arrayWeather = '';
	function handleInput(event) {
		city = event.target.value;
	}
    async function fetchData() {
        if(city!=''){
            search=true;
            const response = await fetch(
			`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=630cde63b6f9f0dae6abcca158c8a36b`
		);
		    city='';
		    const data = await response.json();
            arrayWeather = data;
            if(response.status===404){
                arrayWeather=null;
            }
        }else{
            search=false;
        }
    }
</script>
<nav>
    <strong>Weather App</strong>
</nav>
<main>
    <div class="div-form__city">
        <input class={search ? "input-check":"input-fail"} type="text" value={city} on:input={handleInput} />
	    <button on:click={() => fetchData()}><i class="material-icons">search</i> </button>
    </div>
	{#await arrayWeather}
		<p>cargando...</p>
	{:then weather}
		{#if weather != '' && weather!=null}
			<WeatherDetail {arrayWeather} />
		{:else}
            {#if weather==null}
                <p>city not found</p>
            {/if}
			<div />
		{/if}
	{/await}
</main>

<style>
    /* your styles go here */
    nav{
        position: fixed;
        top: 0px;
        left: 0px;
        right: 0px;
        height: 4rem;
        padding-left: 5px;
        background-color:#c46;
    }
    main{
        margin-top: 4rem;
    }
    nav > strong{
        font-size: 30px;
        width: 100%;
        text-align: center;
    }
	input[type='text'] ,input[type=text]:not(.browser-default):focus:not([readonly]){
		margin: 5px;
		padding: 0px 10px;
        width: 100%;
        height: 3rem;
		border-radius: 15px;
		
		-webkit-box-shadow: none;
        box-shadow: none;
    }
    .input-check{
        border: 3px solid #5DADE2  !important;
        transition: border 1s;
    }
    .input-fail{
        border: 3px solid #EC7063 !important; 
        transition: border 1s;
    }
    button{
        width: 3rem;
        background-color:#c46;
        border: none;
        border-radius: 35px;
        height: 3rem;
        color: #fff;
        font-size: 90%;
        line-height: 0;
    }
    button:hover{
        background-color:#c43;
        color: #000;
        box-shadow: 2px 2px 10px 5px #D5D8DC;
    }
    .div-form__city{
        padding: 5px;
        width: 100%;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
    }
    p{
        font-size: 30px;
        text-align: center;
    }
</style>
