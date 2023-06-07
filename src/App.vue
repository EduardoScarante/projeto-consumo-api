<script>
import { RouterLink, RouterView } from 'vue-router'
import lottie1 from "./lottie/love-dog.json"
import lottie2 from "./lottie/love-sheep.json"


export default {
  data() {
    return {
      lottie1,
      lottie2,

      AnuncioApiLove: false,
      nome1: '',
      nome2: '',
      resApi: ''
    }
  },
  methods: {
    openLoveApi() {
      this.AnuncioApiLove = !this.AnuncioApiLove
    },
    async calculateLoveApi() {

      const url = `https://love-calculator.p.rapidapi.com/getPercentage?sname=${this.nome1}&fname=${this.nome2}`;
      const options = {
        method: 'GET',
        headers: {
          'X-RapidAPI-Key': '311ed1e4a9msh8fb52b3af94b7cep178b83jsnaaaec4ea33b7',
          'X-RapidAPI-Host': 'love-calculator.p.rapidapi.com'
        }
      }

      const response = await fetch(url, options);
      const result = await response.json();
      this.resApi = result
    }
  }
}
</script>


<template>
  <main>
    <nav>
      <RouterLink to="/">
        <span class="material-symbols-outlined">
          home
        </span>
      </RouterLink>
    </nav>

    <RouterView />
    <!--     
                              <lottie-player :src="lottie" speed="1" style="width: 100vw; height: auto" loop autoplay>
                              </lottie-player> -->

    <div class="anuncio" @click="openLoveApi">
      love
    </div>

    <div v-show="AnuncioApiLove" class="modalApiLove">
      <div class="modal">

        <div class="inputUser">
          <p><b>Calculadora do Amor!</b></p>
          <div @click="openLoveApi" class="btnClose">X</div>
          <input type="text" placeholder="Digite seu Nome" v-model="nome1">
          <input type="text" placeholder="Digite o Nome do seu Amor!" v-model="nome2">
          <button @click="calculateLoveApi">Calcular</button>

          <div class="res" v-show="(resApi != '')">
            <p>{{ resApi.percentage }}%</p>
            <p>{{ resApi.result }}</p>
          </div>
        </div>


        <lottie-player class="lt1" :src="lottie1" speed="1" style="width: 400px; height: auto" loop autoplay></lottie-player>
        <lottie-player class="lt2" :src="lottie2" speed="1" style="width: 400px; height: auto" loop autoplay></lottie-player>


      </div>
    </div>
  </main>
</template>



<style scoped>
nav {
  width: 95vw;
  height: 50px;
  margin: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* lottie-player {
  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  height: auto;
  z-index: -1;

} */

nav a.router-link-exact-active {
  color: var(red);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

.anuncio {
  position: fixed;
  bottom: 0;
  right: 0;
  padding: 20px;
}

.modalApiLove {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgb(0, 0, 0, 0.3);

  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;

  z-index: 250;

}

.inputUser {
  flex-direction: column;
  justify-content: space-around;

  width: 400px;
  padding: 50px;
  background-color: white;
  border-radius: 10px;

  background-color: lightcoral;
}

.btnClose {
  position: absolute;
  top: 0;
  right: 0;
  padding: 10px;
}

input {
  padding: 10px;
  border: none;
  width: 300px;
  margin-top: 10px;
  margin-bottom: 10px;

  background-color: rgb(255, 198, 198);
}

button {
  background-color: red;
  padding: 20px;
  border-radius: 10px;
  border: none;
  width: 100px;
}

button:hover {
  opacity: 0.8;
}

.lt1{
  position: absolute;
  bottom: 0;
  right: 0;
}
.lt2{
  position: absolute;
  bottom: 0;
  left: 0;
}
</style>
