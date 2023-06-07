<script>
import climaBox from "../components/climaBox.vue";

export default {
  components: {
    climaBox,
  },
  data() {
    return {
      search: this.$route.params.name,
      loading: false,
      imageUrl: [],
      clima: [],
    };
  },
  methods: {
    getImages(url) {
      this.loading = true;

      // Obtem foto do Google usando a API de pesquisa de imagens
      const googleSearchApiKey = "AIzaSyBLq5cUwYO31kXPjCxhaELx_tNXv_TI-ec"; // Chave de API do Google JSON  com pesquisas de até 10 000 requisições por dia se for somente web é ilimitado
      const customSearchEngineId = "163bf32740a0e4962"; // ID de pesquisa personalizado
      const googleSearchUrl = `https://www.googleapis.com/customsearch/v1?key=${googleSearchApiKey}&cx=${customSearchEngineId}&q=${url}&searchType=image`;

      fetch(googleSearchUrl)
        .then((res) => res.json())
        .then((data) => {
          for (let x = 0; x < 10; x++) {
            this.imageUrl.push(data.items[x].link);
          }
        })
        .catch((err) => {
          console.log("error: ", err);
        });
      this.loading = false;
    },
    getClima(a) {
      let url = `https://weather.visualcrossing.com/VisualCrossingWebServices/rest/services/timeline/${a}?unitGroup=metric&key=ZNGGPXU6288M2AFT47884B8LQ&contentType=json`;
      fetch(url)
        .then((e) => e.json())
        .then((data) => {
          for (let x = 0; x < 14; x++) {
            this.clima.push({
              data: data.days[x].datetime,
              tempmin: data.days[x].tempmin,
              tempmax: data.days[x].tempmax,
              tempmedia: data.days[x].temp,
              nascerdosol: data.days[x].sunrise,
              pordosol: data.days[x].sunset,
              humidade: data.days[x].humidity,
              condição: data.days[x].conditions,
              descrição: data.days[x].description,
              precipitação: data.days[x].precip,
              icon: data.days[x].icon.replaceAll("-", ""),
            });
            console.log(data.days[x]);
          }
        })
        .catch((err) => {
          console.log("erro: ", err);
        });
    },
  },
  mounted() {
    //   this.getImages(this.search);
    this.getClima(this.search);
  },
};
</script>

<template>
  <!-- <h3 v-show="loading">ALGO BONITINHO PARA APARECER QUANDO ESTÁ CARREGANDO</h3> -->

  <main>
    <div class="car">
      <div v-for="x of imageUrl">
        <img :src="x" alt="Google Image" key="API_KEY" />
      </div>
    </div>

    <div v-for="x of clima" class="climaBox">
      <climaBox :clima="x" />
    </div>
  </main>
</template>

<style scoped>
main {
  display: flex;
  margin: auto;
  width: 80vw;
  flex-wrap: wrap;
}

.climaBox {
  margin: auto;
}

img {
  height: 250px;
  margin: 10px;
}
.car {
  display: flex;
  margin: auto;
  width: 75vw;
  height: 150px;
  background-color: azure;
  overflow-y: auto;
}
</style>
