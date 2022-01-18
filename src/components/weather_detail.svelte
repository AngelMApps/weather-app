<script>
	// your script goes here
	export let arrayWeather = "";
	console.log("object");
	console.log(arrayWeather);
</script>

<!-- markup (zero or more items) goes here -->
<main class="row">
	<div class="col s12 m4 l4">
		<strong>{arrayWeather.name} - {arrayWeather.sys.country}</strong>
		<img src="https://openweathermap.org/img/wn/{arrayWeather.weather[0].icon}@4x.png" alt="icon" />
		<h3>{arrayWeather.weather[0].description}</h3>
		<h5>clouds: {arrayWeather.clouds.all} </h5>
		<h4>{arrayWeather.main.temp}°C / {arrayWeather.main.humidity}%</h4>
	</div>
	
	<div class="col s12 m6 l4">
		<strong>Coordinates</strong>
		<h3 class="lat-h3">lat: {arrayWeather.coord.lat}</h3>
		<h3 class="lon-h3">lon: {arrayWeather.coord.lon}</h3>
		<strong>Time Zone</strong>
		<h3 class="lat-h3">{arrayWeather.timezone}</h3>
		
	</div>
	<div class="col s12 m3 l3">
		<strong>Wind</strong>
		<h3 style="color: #aedbff; margin-top: 5px;margin-bottom: 5px;">deg: {arrayWeather.wind.deg}</h3>
		<h3 style="color: #e2cbff;margin-top: 5px;margin-bottom: 5px;">gust: {arrayWeather.wind.gust} </h3>
		<h3 style="color: #91fdf8;margin-top: 5px;margin-bottom: 5px;">speed: {arrayWeather.wind.speed}</h3>
	</div>
	<div class=" div-temp col s12 m4 l4">
		<strong>Max Temperature</strong>
		<h3 style="color: #aedbff;">{arrayWeather.main.temp_max}°C</h3>
		<strong>Max Temperature</strong>
		<h3 style="color: #e2cbff;">{arrayWeather.main.temp_min}°C</h3>
		<strong>Pressure</strong>
		<h3 style="color: #91fdf8;">{arrayWeather.main.pressure}</h3>
	</div>
	
</main>
<style>
	div {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		background-color: #2b3061;
		border-radius: 8px;
		padding: 10px !important;
		margin: 10px;
		width: 200px;
		box-shadow: 5px 5px 20px 5px rgba(0,0,0,0.2);
	}
	strong {
		font-size: 30px;
		color: #fff;
	}
	h3{
		font-size: 25px;
		margin: 0px;
		color: #aedbff;
	}
	h4{
		font-size: 20px;
		margin: 10px;
		color: #91fdf8;
	}
	h5{
		color: #e2cbff;
		font-size: 18px;
	}
	img {
		width: 100px;
	}
	.lat-h3,.lon-h3{
		text-align: center;
		margin-top: 4px;
		margin-bottom: 4px;
		color: #49ecec;
	}
	@media only screen and (max-width:796px){
		.div-temp>strong{
			font-size: 28px;
		}
	}
	@media only screen and (max-width:739px){
		.div-temp>strong{
			font-size: 25px;
		}
	}
	@media only screen and (max-width:668px){
		.div-temp>strong{
			font-size: 22px;
		}
	}
</style>
