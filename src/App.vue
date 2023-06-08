<script>
import { RouterLink, RouterView } from "vue-router";

import icon from "./icons/love-message.png";

import loveApi from "./components/apiLove.vue"

export default {
  components:{
    loveApi
  },
  data() {
    return {
      icon,
      AnuncioApiLove: false,
    };
  },
  methods: {
    HandleModalLoveApi() {
      this.AnuncioApiLove = !this.AnuncioApiLove;
      console.log(this.AnuncioApiLove);
    }
  },
};
</script>

<template>
  <main>
    <nav>
      <RouterLink to="/">
        <span class="material-symbols-outlined"> home </span>
      </RouterLink>
      <RouterLink to="/info">
        <span class="material-symbols-outlined"> info </span>
      </RouterLink>
      <RouterLink to="/creators">
        <span class="material-symbols-outlined"> logo_dev </span>
      </RouterLink>
      
    </nav>

    <RouterView />

    <div class="anuncio" @click="HandleModalLoveApi">
      <img :src="icon" alt="" />
    </div>

    <loveApi v-on:closeModal="HandleModalLoveApi" v-if="AnuncioApiLove"></loveApi>

    
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

img {
  height: 60px;
  transform: rotateY(180deg); 
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

  cursor: pointer;
}

</style>
