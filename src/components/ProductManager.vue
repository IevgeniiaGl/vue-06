<template>
 <h2>Task 05</h2>
<div class='manager-container'>
    <div class="filter-block"><product-filters
     :product-list="notebooksList"
    v-model:brand.check="filteredBrand"
    v-model:seller.check="filteredSeller"
    
    /> </div>
    <div><product-list :cards-list-data="filteredProducts"/> </div>
</div>





</template>

<script>

import { notebooksList} from "@/constants/3_data_notebooks";
import ProductFilters from "./ProductFilters.vue";
import ProductList from "./ProductList.vue";



export default{
  name:'ProductManager',

  components:{
    ProductFilters,
    ProductList,

  },
  props: {
        productList: {
            type: Array,
            default: () => [],
        },
    },

  data(){
    return{
      notebooksList,
       filteredBrand: [],
            filteredSeller: [],

  }},
  computed: {
        filteredProducts() {
            if (this.filteredBrand.length === 0 && this.filteredSeller.length === 0) {
                return this.notebooksList
            }

            return this.notebooksList.filter((product) => {
                const isBrandMatch = this.filteredBrand.length === 0 || this.filteredBrand.includes(product.brand)
                const isSellerMatch = this.filteredSeller.length === 0 || this.filteredSeller.includes(product.seller)
                return isBrandMatch && isSellerMatch
            })
        },
    },

}

</script>

<style>
.manager-container{
    display: flex;
    gap: 30px;
}
.filter-block{
    flex: 0 1 300px;
}
</style>
