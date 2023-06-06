<script>


export default{
    data(){
        return{
            name: this.$route.params.name
        }
    }
}

</script>

<template>

    Detalhes! :)
    {{ name }}

</template>