<template>
    <div class="container-fluid pt-5 ">
        <div class="container">
            <div class="row">
                <div class="col-12">
                    list
                </div>
            </div>
            <div class="row text-center ms-6">
                <AppCard/>
            </div>
        </div>
    </div>
    
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
    div.container-fluid{
        background-color: #d48f38;
        height: 800px;
    }

    div.container{
        background-color: white;
        width: 1200px;
        height: 700px;
    }
</style>