<template>
    <div class="container-fluid pt-5 ">
        <div class="row">
            <div class="col-12 ps-5 pb-5 justify-content-center">
                <CharacterDropmenu/>
            </div>
        </div>
        <div class="container">
            <div class="row">
                
            </div>
            <div class="row text-center ms-6">
                <AppCard v-for="card in cardList"
                        :cardName="card.name"
                        :cardSpecies="card.archetype"
                        :cardImg="card.card_images[0].image_url"
                />
            </div>
        </div>
    </div>
    
</template>
<script>
import AppCard from './AppCard.vue'
import CharacterDropmenu from './CharacterDropmenu.vue'
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
        AppCard,
        CharacterDropmenu
    },
    created(){
                axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
                .then( (response) => {
                console.log(response.data.data);
                this.cardList = response.data.data
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
        
    }

    div.container{
        background-color: white;
        width: 1200px;
        
    }
</style>