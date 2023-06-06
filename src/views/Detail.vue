<script>
export default {
  data() {
    return {
      campoPesquisa: this.$route.params.name,
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
          const googleSearchUrl = `https://www.googleapis.com/customsearch/v1?key=${googleSearchApiKey}&cx=${customSearchEngineId}&q=${url}&searchType=image`;
          console.log(googleSearchUrl)

          fetch(googleSearchUrl)
            .then((res) => res.json())
            .then((data) => {
              if (data.items && data.items.length > 0) {
                const imageUrl = data.items[2].link;
                this.imageUrl = imageUrl;
              }
              console.log(data);
            });

          this.loading = false;
        },
    
  },
  mounted() {
    this.getImages(this.campoPesquisa);
  },
};
</script>

<template>
  <h3 v-show="loading">ALGO BONITINHO PARA APARECER QUANDO ESTÁ CARREGANDO</h3>
{{ campoPesquisa }}
  <div v-if="imageUrl">
    <img :src="imageUrl" alt="Google Image" key="API_KEY" />
  </div>
</template>
