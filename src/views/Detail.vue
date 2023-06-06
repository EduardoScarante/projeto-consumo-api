<script>
export default {
    data() {
        return {
            loading: false,
            imageUrl: [],
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
                        this.imageUrl.push(data.items[x].link)
                    }
                });
            this.loading = false
        },
    },
    mounted() {
        this.getImages(this.$route.params.name);
    },
};
</script>

<template>
    <h3 v-show="loading">ALGO BONITINHO PARA APARECER QUANDO ESTÁ CARREGANDO</h3>

    <div class="car">
        <div v-for="x of imageUrl">
            <img :src="x" alt="Google Image" key="API_KEY" />
            
        </div>
    </div>

</template>

<style scoped>
img {
    height: 250px;
    margin: 10px;
}

.car{
    display: flex;
    margin: auto;
    width: 75vw;
    overflow-y: auto;
}
</style>
