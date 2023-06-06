<script>
import search from "../components/search.vue";

export default {
  components: {
    search,
  },
  data() {
    return {
      cidades: [],
      filteredCidades: [],
      filtro: "",
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
  <main>

    <h2>Cidades ;)</h2>

    <input type="text" v-model="filtro" @keyup="handleFilter" />

    <br>

    <div class="boxFilter">
      <div v-for="x of filteredCidades">
        <search @click="handleClickDetail" :filteredCidades="x" />
      </div>
    </div>


  </main>
</template>

<style scoped>
main {
  flex-direction: column;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

input {
  height: 20px;
  width: 650px;
  border: none;
  padding: 20px;
  background-color: rgb(238, 238, 238);

  border-radius: 5px;
}

.boxFilter{
  height: 500px;
  overflow: auto;
  padding-top: 30px;
}
</style>