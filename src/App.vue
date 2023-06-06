<script>
import { RouterLink, RouterView } from 'vue-router'
import lottie from "./lottie/Fundo.json"

export default {
  data() {
    return {
      lottie: lottie
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
  </main>
</template>



<style scoped>
nav{
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


</style>
