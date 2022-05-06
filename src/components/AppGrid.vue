<template>
    <section class="container">
        <div class="row">
            <div v-for="album in albumList" :key="album.id"  class="col-6 col-md-4 col-lg-2 my-5"> 
                <app-card :item="album"/>
            </div>
        </div>
    </section>
</template>

<script>
import axios from "axios"
import AppCard from './AppCard.vue'

export default {
    name: "AppGrid",
    components: { 
        AppCard 
    },
    data(){
        return{
            albumList: [],
        }
    },
    mounted(){
        axios.get("https://flynn.boolean.careers/exercises/api/array/music").then((res)=>{
            console.log(res.data.response)
            this.albumList = res.data.response
        }).catch((err)=>{
            console.log(err)
        })
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars.scss';

.col-lg-2{
    flex: 0 0 18%;
    display: flex;
}

</style>