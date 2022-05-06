<template>
    <section class="container">
        <app-loader v-if="loader"/>
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
import AppLoader from './AppLoader.vue'

export default {
    name: "AppGrid",
    components: { 
        AppCard,
        AppLoader 
    },
    data(){
        return{
            albumList: [],
            loader: true,
        }
    },
    mounted(){
        this.loader = true;
        setTimeout(()=>{
            axios.get("https://flynn.boolean.careers/exercises/api/array/music").then((res)=>{
                console.log(res.data.response)
                this.albumList = res.data.response
                this.loader = false;
            }).catch((err)=>{
                console.log(err)
                this.loader = false;
            })
        },2000)
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