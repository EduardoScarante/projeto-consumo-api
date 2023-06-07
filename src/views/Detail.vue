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
            climaCarosel: [],
            index: 0
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
                }).catch(err => {
                    console.log("error: ", err)
                })
            this.loading = false
        },
        getClima(a) {
            let url = `https://weather.visualcrossing.com/VisualCrossingWebServices/rest/services/timeline/${a}?unitGroup=metric&key=ZNGGPXU6288M2AFT47884B8LQ&contentType=json`
            fetch(url)
                .then(e => e.json())
                .then(data => {
                    for (let x = 0; x < 10; x++) {
                        this.clima.push({
                            "index": x,
                            "data": data.days[x].datetime.split("-").reverse().join("/"),
                            "tempmin": data.days[x].tempmin + ("°"),
                            "tempmax": data.days[x].tempmax + ("°"),
                            "tempmedia": data.days[x].temp + ("°"),
                            "nascerdosol": data.days[x].sunrise,
                            "pordosol": data.days[x].sunset,
                            "humidade": data.days[x].humidity + "%",
                            "condição": data.days[x].conditions,
                            "descrição": data.days[x].description,
                            "precipitação": data.days[x].precip + "mm",
                            "icon": data.days[x].icon.replaceAll("-", "")

                        })
                    }

                    for (let x = 0; x < 3; x++) {
                        this.climaCarosel.push({
                            "index": x,
                            "data": data.days[x].datetime.split("-").reverse().join("."),
                            "tempmin": data.days[x].tempmin + ("°"),
                            "tempmax": data.days[x].tempmax + ("°"),
                            "tempmedia": data.days[x].temp + ("°"),
                            "nascerdosol": data.days[x].sunrise,
                            "pordosol": data.days[x].sunset,
                            "humidade": data.days[x].humidity + "%",
                            "condição": data.days[x].conditions,
                            "descrição": data.days[x].description,
                            "precipitação": data.days[x].precip + "mm",
                            "icon": data.days[x].icon.replaceAll("-", "")

                        })
                    }
                }).catch(err => {
                    console.log("erro: ", err)
                })
        },
        indexMenos() {
            if (this.index == 0) return
            this.index--
            this.climaCarosel = this.clima.slice(this.index, this.index + 3)
        },
        indexMais() {
            if (this.index == 7) return
            this.index++
            this.climaCarosel = this.clima.slice(this.index, this.index + 3)
        }
    },
    mounted() {
        //this.getImages(this.search);
        this.getClima(this.search);
    },
};
</script>

<template>
    <main>
        <div class="caroselImg">
            <div v-for="x of imageUrl">
                <img :src="x" alt="Google Image" />
            </div>
        </div>

        <div class="climaBox">
            <div @click="indexMenos" class="arrow">
                &lt
            </div>
            <div v-for="x of climaCarosel">
                <climaBox :clima="x" />
            </div>
            <div @click="indexMais" class="arrow">
                >
            </div>
        </div>

    </main>
</template>

<style scoped>
main {
    display: flex;
    flex-direction: column;
}

img {
    height: 250px;
    margin: 10px;
}

.caroselImg {
    display: flex;
    margin: auto;
    width: 90vw;
    height: 300px;
    background-color: white;
    box-shadow: 8px 8px 24px #c5c5c5,
        -8px -8px 24px #fbfbfb;
    overflow-y: auto;
    border-radius: 10px;
}


/* CLIMA */
.climaBox {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    margin: auto;

    width: 80vw;

}


.arrow {
    margin: 10px;


    display: flex;
    align-items: center;
    justify-content: center;

    width: 50px;

    border-radius: 10px;
    background: rgb(255, 255, 255, 0.2);
    font-weight: 700;
    font-size: 30px;
    box-shadow: 8px 8px 24px #c5c5c5,
        -8px -8px 24px #fbfbfb;

    transition: 0.2s;

    user-select: none;
}

.arrow:hover {
    background-color: rgb(245, 245, 245);
}
</style>
