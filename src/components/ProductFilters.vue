<template>
    <div>
        <div :style="{ border: addBorderSeller }" class="filter-block" >
            <h3>Магазин:</h3>
            <div v-for="seller in sellersList" :key="seller">
                <input type="checkbox" v-model="checkedSeller" :value="seller" />
                {{ seller }}
            </div>
        </div>
    </div>
    <div>
        <div :style="{ border: addBorderBrand }" class="filter-block">
            <h3>Бренд:</h3>
            <div v-for="brand in brandsList" :key="brand">
                <input type="checkbox" v-model="checkedBrand" :value="brand" />
                {{ brand }}
            </div>
        </div>
    </div>
</template>

<script>
import { notebooksList} from "@/constants/3_data_notebooks";

export default {
    name: 'ProductFilters',

    props: {
        productList: {
            type: Array,
            required: true,
        },
        brand: {
            type: Array,
            required: true,
        },
        brandModifiers: {
            default: () => ({}),
        },
        seller: {
            type: Array,
            required: true,
        },
        sellerModifiers: {
            default: () => ({}),
        },
    },
    data() {
        return {
           notebooksList,
        }
    },

    computed: {
        brandsList() {
            const brandsList = notebooksList.reduce((uniqueBrands, product) => {
                if (!uniqueBrands.includes(product.brand)) {
                    uniqueBrands.push(product.brand)
                }
                return uniqueBrands
            }, [])

            return brandsList
        },
        sellersList() {
            const sellersList = notebooksList.reduce((uniqueSellers, product) => {
                if (!uniqueSellers.includes(product.seller)) {
                    uniqueSellers.push(product.seller)
                }
                return uniqueSellers
            }, [])
            return sellersList
        },
        checkedBrand: {
            get() {
                return this.brand
            },
            set(val) {
                this.$emit('update:brand', val)
            },
        },
        checkedSeller: {
            get() {
                return this.seller
            },
            set(val) {
                this.$emit('update:seller', val)
            },
        },
        addBorderBrand() {
            if (this.brandModifiers.check) {
                if (this.checkedBrand.length === 0) {
                    return '2px solid green'
                     
                }
            }
            return null
        },
        addBorderSeller() {
            if (this.sellerModifiers.check) {
                if (this.checkedSeller.length === 0) {
                    return '2px solid green'
                }
            }
            return null
        },
    },
}
</script>

<style lang="scss" scoped>
.filter-block{
    margin-bottom: 20px;
    padding: 10px;
}
.green-border{
    border: 1px solid green;
}

</style>