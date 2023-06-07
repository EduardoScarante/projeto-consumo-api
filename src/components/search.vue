<script>
export default {
    props: {
        filteredCidades: Object,
    },
    data() {
        return {}
    }
}
</script>


<template>
    <main class="content" :id="filteredCidades.nome">
        {{ filteredCidades.nome }} <br>
        {{ filteredCidades.estado }} / {{ filteredCidades.UF }}
    </main>
</template>

<style scoped>
.content {
    display: flex;
    justify-content: center;
    align-items: center;
    
    width: 500px;
    height: 100px;
    margin-bottom: 10px;
    border-radius: 5px;
    margin: 10px;

    background-color: rgb(236, 236, 236) !important; 
    box-shadow: 1px 1px 3px lightgray;
}
</style>