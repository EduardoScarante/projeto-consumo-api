<script>

import snow from '@/icons/snow.png';
import rain from '@/icons/rain.png';
import fog from '@/icons/fog.png';
import wind from '@/icons/wind.png';
import cloudy from '@/icons/cloudy.png';
import partlycloudyday from '@/icons/partlycloudyday.png';
import partlycloudynight from '@/icons/partlycloudynight.png';
import clearday from '@/icons/clearday.png';
import clearnight from '@/icons/clearnight.png';

export default {
    data() {
        return {
            snow,
            rain,
            fog,
            wind,
            cloudy,
            partlycloudyday,
            partlycloudynight,
            clearday,
            clearnight,
            icon: ''
        }
    },
    methods: {
        getImg(icon){
            return this[icon]
        }
    },
    props: {
        clima: Object
    }
}
</script>

<template>
    <main>
        <h1> {{ clima.data }} </h1>
        <div class="temp">
            <h3> Media: {{ clima.tempmedia }} </h3>
            <h3> Min: {{ clima.tempmin }} </h3>
            <h3> Max: {{ clima.tempmax }} </h3>
        </div>
        <div class="temp">
            <h3> nascer-do-sol: {{ clima.nascerdosol }} </h3>
            <h3> por-do-sol: {{ clima.pordosol }} </h3>
        </div>
        <div class="temp">
            <h3> humidade: {{ clima.humidade }} </h3>
            <h3> precipitação: {{ clima.precipitação }} </h3>
        </div>
        <h3> descrição: {{ clima.descrição }} </h3>

        <img :src="getImg(clima.icon)" alt="">

    </main>


    icone: {{ clima.icon }}
</template>

<style scoped>
main {
    background-color: rgb(240, 240, 240);
    box-shadow: 1px 1px 2px lightgray;
    width: 250px;
    height: 200px;

    margin: 10px;

    font-size: 8px;

    display: flex;
    align-items: center;
    flex-direction: column;

}

img {
    width: 50px;
    height: 50px;
}

.temp {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
}
</style>