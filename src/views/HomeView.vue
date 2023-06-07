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
      mostarbox: false,
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
        this.mostarbox = false
        return;
      }

      this.mostarbox = true
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
  <main class="container">
    <div id="imagens">
      <img id="logo" src="../logos/iconBranco.png" />
      <img id="text" src="../logos/textoHome.png" />
    </div>

    <input
      type="text"
      v-model="filtro"
      @keyup="handleFilter"
      placeholder="Busque por uma cidade do Brasil..."
    />

    <br />

    <div class="boxFilter" v-show="mostarbox">
      <div v-for="x of filteredCidades">
        <search @click="handleClickDetail" :filteredCidades="x" />
      </div>
    </div>
  </main>
</template>

<style scoped>
.container {
  flex-direction: column;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;

  background: linear-gradient(0deg, rgb(1, 55, 136) 8%, rgba(0,45,114,1) 100%);

  height: 94vh;
}

#imagens {
  flex-direction: row;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

img#logo {
  height: 250px;
}

img#text {
  height: 90%;
}

input {
  height: 20px;
  width: 37%;
  min-width: 400px;
  border: none;
  padding: 20px;
  background-color: rgb(238, 238, 238);

  border-radius: 5px;
}

input:focus {
  box-shadow: 0 0 0 1px rgba(214, 214, 214, 0.562);
  outline: 0;
}

.boxFilter {
  height: 300px;
  overflow: auto;
}

::placeholder {
  -webkit-filter: grayscale(100%);
  filter: grayscale(100%);
  filter: gray;
}
</style>
