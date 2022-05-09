<template>
    <section class="container">
        <app-select @mySelect="setSelectText($event)" :albumGenres="genres"/>
        <app-loader v-if="loader"/>
        <div class="row">
            <div v-for="album in filteredAlbum" :key="album.id"  class="col-6 col-md-4 col-lg-2 my-5"> 
                <app-card :item="album"/>
            </div>
        </div>
    </section>
</template>

<script>
import axios from "axios"
import AppCard from './AppCard.vue'
import AppLoader from './AppLoader.vue'
import AppSelect from './AppSelect.vue'

export default {
    name: "AppGrid",
    components: { 
        AppCard,
        AppLoader,
        AppSelect 
    },
    data(){
        return{
            albumList: [],
            searchText:"",
            loader: true,
            genres: [],
        }
    },
    methods:{
        setSelectText(txt){
            this.searchText = txt;
        }
    },
    computed:{
        filteredAlbum(){
            if(this.searchText === "") return this.albumList;
            return this.albumList.filter((el)=> {
                return el.genre === this.searchText
            });
                
        }
    },
    mounted(){
        this.loader = true;
        
            axios.get("https://flynn.boolean.careers/exercises/api/array/music").then((res)=>{
                console.log(res.data.response)
                this.albumList = res.data.response
                this.albumList.forEach((el)=>{
                    if(!this.genres.includes(el.genre)){
                        this.genres.push(el.genre);
                    }
                })
                this.loader = false;
            }).catch((err)=>{
                console.log(err)
                this.loader = false;
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
.container{
    padding-top: 50px;
}

</style>