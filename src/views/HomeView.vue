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
        this.mostarbox = false;
        return;
      }

      this.mostarbox = true;
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
      <img id="logo" src="../logos/AttemptICONazul.png" />
      <img id="text" src="../logos/AttemptTEXTO(2).png" />
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

  background: linear-gradient(
    360deg,
    #002d72 0%,
    #0055d9 100%
  );

  height: 94.6vh;
}

#imagens {
  flex-direction: column;
  display: flex;
  align-items: center;
  text-align: center;

  height: 520px;
}

img#logo {
  width: 18%;
  min-width: 200px;
}

img#text {
  width: 42%;
  min-width: 400px;
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
  height: 25vh;
  overflow: auto;
  cursor: pointer;
}

/* NAV BAR PERSONALIZADA */

.boxFilter::-webkit-scrollbar {
  width: 4px;
}

.boxFilter::-webkit-scrollbar-track {
  background: #88888800;
  border-radius: 6px;
}

.boxFilter::-webkit-scrollbar-thumb {
  background: #ffffff;
  border-radius: 6px;
}
</style>
