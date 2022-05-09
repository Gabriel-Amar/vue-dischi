<template>
    <div>
        <div class="input-group">
            <select name="genre" id="genre" v-model="selectInput" @change="changeSelect">
                <option value="">All</option>
                <option :value="genre" v-for="genre in albumGenres" :key="genre">
                    {{genre}}
                </option>
            </select>
        </div>
    </div>
</template>

<script>
export default {
    name: "AppSelect",
    props:[
        "albumGenres"
    ],
    data(){
        return{
            selectInput: "",
        }
    },
    methods:{
        changeSelect(){
            this.$emit("mySelect", this.selectInput)
        }
    },
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars.scss';

select{
    height: 61px;
    width: 20%;
    font-size: 20px;
    border-radius: 20px;
    padding: 7px;
}


</style>