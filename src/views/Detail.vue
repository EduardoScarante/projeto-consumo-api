<script>
export default{
    data(){
        return{
            a: this.$route.params.name
        }
    }
}

</script>

<template>
   {{ a }}
</template>

<!-- <script>
export default {
  data() {
    return {
      loading: false,
      imageUrl: "", //Propriedade para armazenar a URL da imagem
    };
  },
  methods: {
    getImages(url) {
      this.loading = true;

          // Obtem foto do Google usando a API de pesquisa de imagens
          const googleSearchApiKey = "AIzaSyBLq5cUwYO31kXPjCxhaELx_tNXv_TI-ec"; // Chave de API do Google JSON  com pesquisas de até 10 000 requisições por dia se for somente web é ilimitado
          const customSearchEngineId = "163bf32740a0e4962"; // ID de pesquisa personalizado
          const googleSearchUrl = `https://www.googleapis.com/customsearch/v1?key=${googleSearchApiKey}&cx=${customSearchEngineId}&q=${/*NOME DA VARIAVEL CIDADE*/}&searchType=image`;

          fetch(googleSearchUrl)
            .then((res) => res.json())
            .then((data) => {
              if (data.items && data.items.length > 0) {
                const imageUrl = data.items[1].link;
                this.imageUrl = imageUrl;
              }
              console.log(data.items);
            });

          this.loading = false;
        },
    },
  };
  mounted() {
    const id = this.$route.params.id; // acho que é assim
    this.getImages(`
    // ADIDIONAR A ROTA COM ID DA CIDADE //
    `);
  },
};
</script>

<template>
  <h3 v-show="loading">ALGO BONITINHO PARA APARECER QUANDO ESTÁ CARREGANDO</h3>

  <div v-if="imageUrl">
    <img :src="imageUrl" alt="Google Image" key="API_KEY" />
  </div>
</template>
 -->