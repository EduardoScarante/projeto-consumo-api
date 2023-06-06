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

<style>
main {
    width: 100px;
    margin-bottom: 10px;
    background-color: lightcyan;
    border-radius: 5px;
    padding: 10px;
}
</style>