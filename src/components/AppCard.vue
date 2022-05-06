<template>
    <div class="text-center">
        <img :src="item.poster" alt="">
        <h3 class="text-light">{{item.title}}</h3>
        <p>{{item.author}}</p>
        <p>{{item.year}}</p>
    </div>
</template>

<script>
export default {
    name: "AppCard",
    props:[
        "item"
    ]
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars.scss';
p{
    color: $p-color;
}
h3{
    text-transform: uppercase;
    padding-left: 5px;
    padding-right: 5px;
}
img{
    width: 210px;
    padding: 20px;
}
.text-center{
    background-color: $hd-color;
}
</style>