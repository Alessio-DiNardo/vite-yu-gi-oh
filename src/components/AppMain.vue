<template>
    <div>
        <h2>AppMain</h2>
    </div>
    <AppCard/>
</template>
<script>
import AppCard from './AppCard.vue'
import {store} from '../store'
import axios from 'axios';
export default {
    name: 'AppMain',
    data() {
        return {
            store,
        },
        {
            cardList: [],
        }
    },
    components:{
        AppCard
    },
    created(){
                axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
                .then( (response) => {
                console.log(response.data.results);
                this.cardList = response.data.results
            })
                .catch(function (error) {
                console.log(error);
        })
    }
}
</script>
<style lang="scss" scoped>
    
</style>