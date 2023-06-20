<template>
        <div class="dropdown-center">
            <button class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                Centered dropdown
            </button>
        <ul class="dropdown-menu">
            <li><a class="dropdown-item" href="#">Action</a></li>
            <li><a class="dropdown-item" href="#">Action two</a></li>
            <li><a class="dropdown-item" href="#">Action three</a></li>
        </ul>
        </div>

</template>
<script>
import {store} from '../store.js';
import axios from 'axios';

export default {
name: 'CharacterDropmenu',

components: {
    store
},
data() {
    return {
        store,
        archetypeList: [],
    }
},

created(){
    axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php').then((response) =>{
        this.archetypeList = response.data;
        this.archetypeList = this.archetypeList.slice(0, 6);
        console.log(this.archetypeList);
    })
    .catch(function (error) {
        console.log(error);
    });
}
}
</script>
<style lang="scss" scoped>

</style>