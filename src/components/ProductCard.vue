
<template>
<div class='card'>
    <a :href='cardData.link'>
        <div class="image"><img :src="cardData.imgSrc"></div>
        <div class="title">{{cardData.title}}</div>
        <div class="current-price"> {{cardData.price}}₴</div>
    </a>
</div>
    
</template>

<script>
    export default {
        name:'ProductCard',

        props:{
            cardData:{
                type:Object,
                default:()=>({})
            }
        }
    }
</script>

<style lang="scss" scoped>
.card {
    color: #000000;
    text-decoration: none;
    border: 1px solid #656565;
    padding: 20px;
  
    }
.title{
   font-size: 20px;
   color: rgb(28, 28, 28);
   font-weight: 700;
   margin-bottom: 10px;
   min-height: 60px;

}
.image {
    text-align: center;
    height: 200px;
    img{
    max-width: 200px;
    border-radius: 10px;
}
}


	
		



</style>