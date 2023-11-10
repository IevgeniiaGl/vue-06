<template>
    <div class='panel'>
    <product-card v-for="card in cardsListData"  :key="card.id" :card-data="card"  />
    </div>
</template>

<script>
import ProductCard from './ProductCard.vue'

    export default {
        name:'ProductList',
        components:{ ProductCard},
        props:{
            cardsListData:{
            type:Array,
            default:() => [],
            }
        }
    }
</script>

<style lang="css" scoped>
.panel{
  display: grid;
   grid-template-columns: repeat(3, 1fr);

 
}
   

</style>