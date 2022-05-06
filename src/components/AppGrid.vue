<template>
    <section class="container">
        <div class="row">
            <div v-for="album in albumList" :key="album.id" class="col-6 col-md-4 col-lg-2 ">
                
            </div>
        </div>
    </section>
</template>

<script>
import axios from "axios"
export default {
    name: "AppGrid",
    data(){
        return{
            albumList: [],
        }
    },
    mounted(){
        axios.get("https://flynn.boolean.careers/exercises/api/array/music").then((res)=>{
            this.albumList = res.data
        }).catch((err)=>{
            console.log(err)
        })
    }
}
</script>

<style lang="scss" scoped>

</style>