<script>
import Cards from "./components/Cards.svelte";
import { onMount } from 'svelte';
const stormGlassApiKey = import.meta.env.VITE_STORM_GLASS_API_KEY;
const openWeatherMapApiKey = import.meta.env.VITE_OPENWEATHERMAP_API_KEY;

  let waterTemperature;
  let airTemperature;
  let uvIndex;

  const lat = 42.4;
  const lon = -8.8;
  const stormGlassUrl = `https://api.stormglass.io/v2/weather/point?lat=${lat}&lng=${lon}&params=waterTemperature`;
  const openWeatherMapUrl = `https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&appid=${openWeatherMapApiKey}&units=metric`;
  const openWeatherMapUvUrl = `https://api.openweathermap.org/data/2.5/uvi?lat=${lat}&lon=${lon}&appid=${openWeatherMapApiKey}`;

  onMount(async () => {
    try {
      const [stormGlassResponse, openWeatherMapResponse, openWeatherMapUvResponse] = await Promise.all([
        fetch(stormGlassUrl, {
          headers: {
            'Authorization': stormGlassApiKey
          }
        }),
        fetch(openWeatherMapUrl),
        fetch(openWeatherMapUvUrl)
      ]);

      const stormGlassData = await stormGlassResponse.json();
      const openWeatherMapData = await openWeatherMapResponse.json();
      const openWeatherMapUvData = await openWeatherMapUvResponse.json();

      waterTemperature = stormGlassData.hours[0].waterTemperature.noaa;
      airTemperature = openWeatherMapData.main.temp;
      uvIndex = openWeatherMapUvData.value;
    } catch (error) {
      console.error('Error fetching data:', error);
    }
  });
</script>

<section class="inicio">
  <div class="inicio__bienvenido">
    <div class="inicio__fondo">
      <h3 class="inicio__h3">
        BIENVENIDO
      </h3>
      <p class="inicio__p">En esta aplicación escontrarás las <span class="inicio__span"><strong>climáticas de las playas</strong></span> del municipio de Sanxenxo (Galicia)</p>  
    </div>
 </div>
</section>
<section class="playas">
  <div class="playas__titular">
    <h2 class="playas__h2">
      PLAYAS
    </h2>
    <p class="playas__p">
      Selecciona una playa
    </p>
    <hr class="playas__hr">
  </div>
<div class="cards">
  {#if waterTemperature !== undefined && airTemperature !== undefined && uvIndex !== undefined}
       <Cards {waterTemperature} {airTemperature} {uvIndex}/>
  {:else}
       <p>Loading...</p>
  {/if}
</div>
 

</section>

<style>

.inicio{
  display: flex;
  justify-content: center;
  align-items: center;
}

.inicio__bienvenido{
  background-image: linear-gradient(180deg, rgba(0,0,0,0.50) 50%, #283E41 100%);
  box-shadow: 0 2px 4px 0 rgba(0,0,0,0.50);
  border-radius: 8px;
  margin: 20px;
}

.inicio__fondo{
  background: url(blue_flag_animation.gif);
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  padding: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.inicio__h3{
  font-family: var(--fuente-secundaria);
  color: white;
  text-align: center;
  font-size: 1.5rem;
}

.inicio__p{
  font-family: var(--fuente-primaria);
  color: white;
  text-align: center;
  font-size: 1rem;
  padding-top: 20px;
}

.inicio__span{
  font-weight: 800;
}

/* PLAYAS */

.playas{
  margin: 20px 0px;
}

.playas__titular{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.playas__h2{
  font-family: var(--fuente-secundaria);
  color: white;
  font-size: 1.4rem;
  text-align: center;
}

.playas__p{
  font-family: var(--fuente-primaria);
  color: white;
  text-align: center;
}

.playas__hr{
  border-bottom: 1px solid white;
  width: 78px;
  margin: 20px 0px;
}

/* Cards */

.cards{
  display: flex;
  margin: 20px;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
}

</style>