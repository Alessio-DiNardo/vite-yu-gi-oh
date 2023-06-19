<template>
        <div class="card mb-3 col-3 border border-0">
            <img :src= "cardImg" class="card-img-top" :alt="name + 'image'">
            <div class="card-body">
                <h5 class="card-title">
                    {{cardName}}
                </h5>
                <p class="card-text"><small class="text-body-secondary">
                    {{ cardSpecies }}</small>
                </p>
            </div>
        </div>
        
</template>
<script>
export default {
    name: 'AppCard',
    data() {
        return {
            
        }
    },
    props:{
        cardName: String,
        cardSpecies: String,
        cardImg: String,
    }
}
</script>
<style lang="scss" scoped>
    div.card-body{
        background-color: #d48f38;
        border: none;
    }
</style>