<script>
import search from "../components/search.vue";
import lottie from "../lottie/Fundo.json"
import lottie2 from "../lottie/Fundo2.json"

export default {
  components: {
    search,
  },
  data() {
    return {
      cidades: [],
      filteredCidades: [],
      filtro: "",
      lottie: lottie,
      lottie2: lottie2,
    };
  },
  methods: {
    getIbgeData() {
      fetch("https://servicodados.ibge.gov.br/api/v1/localidades/municipios")
        .then((e) => e.json())
        .then((e) => {
          for (let x in e) {
            this.cidades.push({
              nome: e[x].nome,
              estado: e[x].microrregiao.mesorregiao.UF.nome,
              UF: e[x].microrregiao.mesorregiao.UF.sigla,
            });
          }
        })
        .catch((err) => {
          console.log("error: ", err);
        });
    },
    handleFilter() {
      if (this.filtro.length <= 2) {
        this.filteredCidades = [];
        return;
      }

      this.filteredCidades = this.cidades.filter((e) => {
        return e.nome.toLowerCase().includes(this.filtro.toLowerCase());
      });
    },
    handleClickDetail(e) {
      this.$router.push(`/detalhe/${e.target.id}`);
    },
  },
  mounted() {
    this.getIbgeData();
  },
};
</script>

<template>
  <input type="text" v-model="filtro" @keyup="handleFilter" />

  <div v-for="x of filteredCidades">
    <search @click="handleClickDetail" :filteredCidades="x" />
  </div>

  <lottie-player
    :src="lottie2"
    background="transparent"
    speed="1"
    style="width: 100vw; height: auto"
    loop
    autoplay
  ></lottie-player>
</template>

<style scoped>

lottie-player {
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;

}

</style>