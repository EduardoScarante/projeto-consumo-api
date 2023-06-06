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
    <main :id="filteredCidades.nome">
        {{ filteredCidades.nome }}
        {{ filteredCidades.estado }} / {{ filteredCidades.UF }}
    </main>
</template>

<style scoped>
main {
    width: 500px;
    height: 100px;
    margin-bottom: 10px;
    border-radius: 5px;
    margin: 10px;

    background-color: rgb(236, 236, 236);
    box-shadow: 1px 1px 3px lightgray;
}
</style>