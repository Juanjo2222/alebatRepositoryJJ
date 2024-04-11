<template>
  <div class="container">
    <section class="menu-izq">
    
      <button v-if="!isMenuOpen" class="write-country" @click="toggleMenu">search for places</button>
      
        <img class="weather" v-if="weather_code_current==0 && isMenuOpen==false" src="../assets/sunny.png">
        <img class="weather" v-if="weather_code_current==1 && isMenuOpen==false" src="../assets/cloudy.png">
        <img class="weather" v-if="weather_code_current==2 && isMenuOpen==false" src="../assets/windy.png">
        <img class="weather" v-if="weather_code_current==3 && isMenuOpen==false" src="../assets/rainy.png">
        <img class="weather" v-if="weather_code_current==61 && isMenuOpen==false"  src="../assets/snowy.png">
        <img class="weather" v-if="weather_code_current==80 && isMenuOpen==false"  src="../assets/stormy.png">
        
        <p class= "temp-value" v-if="isMenuOpen==false">{{ temperature_2m }} {{ tempUnits }} </p>
        <p class="date" v-if="isMenuOpen==false">Today - {{ time }}</p>
        <div class="ubicacion">
          <img class="ubication-img" v-if="isMenuOpen==false" src="../assets/ubication.png">
          <p class="country-value" v-if="showInput && isMenuOpen==false"> {{ inputValue }}</p>
        </div>
      <div v-if="isMenuOpen" class="menu-izq-search">
        <div class="cruz-y-texto">
          <input type="text" v-model="inputValue" class="country" placeholder="search location">
          <button class="cruz" @click="toggleMenu">X</button>
        </div>
        <button class="search" @click="showInputValue(); toggleMenu()">Search</button>
     
      </div>
    </section>
    <section class="content-der">
      <div class="botones">
        <button class="celsius" @click="tempUnitChangetoC">ºC</button>
        <button class="farenheit" @click="tempUnitChangetoF">ºF</button>
      </div>
        <section class="cinco-dias">  
          <section class="en-un-dia">
              <p class="days-left">Tomorrow</p>
              <img class="weather-days-left" v-if="weather_code_daily[1]==0" src="../assets/sunny.png">
              <img class="weather-days-left" v-if="weather_code_daily[1]==1" src="../assets/cloudy.png">
              <img class="weather-days-left" v-if="weather_code_daily[1]==2" src="../assets/windy.png">
              <img class="weather-days-left" v-if="weather_code_daily[1]==3" src="../assets/rainy.png">
              <img class="weather-days-left" v-if="weather_code_daily[1]==61"  src="../assets/snowy.png">
              <img class="weather-days-left" v-if="weather_code_daily[1]==80"  src="../assets/stormy.png">
                <section class="days-left-temp">
                  {{ temperature_2m_max[1]}} {{ tempUnits }}
                  <span class="t-min">{{ temperature_2m_min[1]}} {{ tempUnits }} </span>
                </section>
          </section>
          <section class="en-dos-dias">
              <p class="days-left">2 days left</p>
              <img class="weather-days-left" v-if="weather_code_daily[2]==0" src="../assets/sunny.png">
              <img class="weather-days-left" v-if="weather_code_daily[2]==1" src="../assets/cloudy.png">
              <img class="weather-days-left" v-if="weather_code_daily[2]==2" src="../assets/windy.png">
              <img class="weather-days-left" v-if="weather_code_daily[2]==3" src="../assets/rainy.png">
              <img class="weather-days-left" v-if="weather_code_daily[2]==61"  src="../assets/snowy.png">
              <img class="weather-days-left" v-if="weather_code_daily[2]==80"  src="../assets/stormy.png">
                <section class="days-left-temp">
                  {{ temperature_2m_max[2]}} {{ tempUnits }}
                  <span class="t-min">{{ temperature_2m_min[2]}} {{ tempUnits }}</span>
                </section>
          </section>
          <section class="en-tres-dias">
              <p class="days-left">3 days left</p>
              <img class="weather-days-left" v-if="weather_code_daily[3]==0" src="../assets/sunny.png">
              <img class="weather-days-left" v-if="weather_code_daily[3]==1" src="../assets/cloudy.png">
              <img class="weather-days-left" v-if="weather_code_daily[3]==2" src="../assets/windy.png">
              <img class="weather-days-left" v-if="weather_code_daily[3]==3" src="../assets/rainy.png">
              <img class="weather-days-left" v-if="weather_code_daily[3]==61"  src="../assets/snowy.png">
              <img class="weather-days-left" v-if="weather_code_daily[3]==80"  src="../assets/stormy.png">
                <section class="days-left-temp">
                  {{ temperature_2m_max[3]}} {{ tempUnits }}
                  <span class="t-min">{{ temperature_2m_min[3]}}{{ tempUnits }} </span>
                </section>
          </section>
          <section class="en-cuatro-dias">
              <p class="days-left">4 days left</p>
              <img class="weather-days-left" v-if="weather_code_daily[4]==0" src="../assets/sunny.png">
              <img class="weather-days-left" v-if="weather_code_daily[4]==1" src="../assets/cloudy.png">
              <img class="weather-days-left" v-if="weather_code_daily[4]==2" src="../assets/windy.png">
              <img class="weather-days-left" v-if="weather_code_daily[4]==3" src="../assets/rainy.png">
              <img class="weather-days-left" v-if="weather_code_daily[4]==61"  src="../assets/snowy.png">
              <img class="weather-days-left" v-if="weather_code_daily[4]==80"  src="../assets/stormy.png">
                <section class="days-left-temp">
                  {{ temperature_2m_max[4]}} {{ tempUnits }}
                  <span class="t-min">{{ temperature_2m_min[4]}} {{ tempUnits }} </span>
                </section>
          </section>
          <section class="en-cinco-dias">
              <p class="days-left">5 days left</p>
              <img class="weather-days-left" v-if="weather_code_daily[5]==0" src="../assets/sunny.png">
              <img class="weather-days-left" v-if="weather_code_daily[5]==1" src="../assets/cloudy.png">
              <img class="weather-days-left" v-if="weather_code_daily[5]==2" src="../assets/windy.png">
              <img class="weather-days-left" v-if="weather_code_daily[5]==3" src="../assets/rainy.png">
              <img class="weather-days-left" v-if="weather_code_daily[5]==61"  src="../assets/snowy.png">
              <img class="weather-days-left" v-if="weather_code_daily[5]==80"  src="../assets/stormy.png">
                <section class="days-left-temp">
                  {{ temperature_2m_max[5]}} {{ tempUnits }} 
                  <span class="t-min">{{ temperature_2m_min[5]}} {{ tempUnits }}</span>
                </section> 
          </section>
        </section>
        <div class="title-highlights">Today's Highlights</div>
        <section class="today-highlights">
            <section class="highlights-arriba">
              <section class="highlights-arriba-izquierda">
                <p class="wind-spped">Wind Statuts</p>
                <p class= "wind-value" v-if="wind_speed_10m">{{ wind_speed_10m }} {{ windUnits }}</p>
              </section>
              <section class="highlights-arriba-derecha">
                <p class="humidity">Humidity</p>
                <p class= "humid-value" v-if="relative_humidity_2m">{{ relative_humidity_2m }} {{ humidUnits }}</p>
              </section>
            </section>
            <section class="highlights-abajo">
              <section class="highlights-abajo-izquierda">
                <p class="visibillity">Visibility</p>
                <p class= "visib-value" v-if="visibility">{{ visibility }} {{ visibUnits }}</p>
              </section>
              <section class="highlights-abajo-derecha">
                <p class="air">Air pressure</p>
                <p class= "air-value" v-if="surface_pressure">{{ surface_pressure }} {{ airUnits }}</p>
              </section>
            </section>
          </section>
          <p class="final">Created by <span class="nombre">{{nombre}}</span> - devChallenges.io</p>
    </section>
  </div>
</template>

<script setup>

import axios from 'axios';
import { ref } from 'vue';

const BASE_URL_c = 'https://api.open-meteo.com/v1/forecast?latitude=52.52&longitude=13.41&current=temperature_2m,weather_code,surface_pressure,wind_speed_10m,wind_direction_10m&hourly=relative_humidity_2m,visibility&daily=weather_code,temperature_2m_max,temperature_2m_min&wind_speed_unit=mph';
const BASE_URL_f = 'https://api.open-meteo.com/v1/forecast?latitude=52.52&longitude=13.41&current=temperature_2m,weather_code,surface_pressure,wind_speed_10m,wind_direction_10m&hourly=relative_humidity_2m,visibility&daily=weather_code,temperature_2m_max,temperature_2m_min&temperature_unit=fahrenheit&wind_speed_unit=mph';

const nombre="Juan José";

const isMenuOpen = ref(false);

const weather_code_current = ref(null);
const weather_code_daily = ref(null);

const temperature_2m = ref(null);
const temperature_2m_max = ref(null);
const temperature_2m_min = ref(null);

let tempUnits_c = ref(null);
let tempUnits_f = ref(null);
let tempUnits = ref(null);

const time = ref(null);

const visibility = ref(null);
const visibUnits = ref(null);

const wind_speed_10m = ref(null);
const windUnits = ref(null);

const relative_humidity_2m=ref(null);
const humidUnits=ref(null);

const surface_pressure=ref(null);
const airUnits=ref(null);

const showInput = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const showInputValue = () => {

  showInput.value = true;
  
};

const tempUnitChangetoC = () => {

  tempUnits.value = tempUnits_c.value;
  
};

const tempUnitChangetoF = () => {
  
  tempUnits.value = tempUnits_f.value;

};

const getData = async () => {

  try {
    
    const response_c = await axios.get(`${BASE_URL_c}`);

    const response_f = await axios.get(`${BASE_URL_f}`);

    temperature_2m.value = response_c.data.current.temperature_2m;

    temperature_2m_max.value = response_c.data.daily.temperature_2m_max;

    temperature_2m_min.value = response_c.data.daily.temperature_2m_min;

    tempUnits_c.value = response_c.data.current_units.temperature_2m;

    tempUnits_f.value = response_f.data.current_units.temperature_2m;
    
    time.value = response_c.data.current.time;
    
    visibility.value = response_c.data.hourly.visibility[0];

    visibUnits.value = response_c.data.hourly_units.visibility;

    wind_speed_10m.value = response_c.data.current.wind_speed_10m;
   
    windUnits.value = response_c.data.current_units.wind_speed_10m;

    relative_humidity_2m.value = response_c.data.hourly.relative_humidity_2m[0];

    humidUnits.value = response_c.data.hourly_units.relative_humidity_2m;

    surface_pressure.value = response_c.data.current.surface_pressure;

    airUnits.value = response_c.data.current_units.surface_pressure;

    weather_code_current.value = response_c.data.current.weather_code;

    weather_code_daily.value = response_c.data.daily.weather_code;

  } catch (error) {
    console.error('Error al obtener los datos:', error);
  }

};

import { onMounted } from 'vue';
onMounted(()=>getData());

</script>

<style scoped src="./styles.css"></style>

