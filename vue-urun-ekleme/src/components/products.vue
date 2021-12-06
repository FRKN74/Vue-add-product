<template>

    <div class="products">
        <label id="lbl">Ürünler  <br><small style="color :red;" class=" ml-2 mt-1">{{ info }}</small></label>
        <hr>
        <app-product v-for="product in productsList ">
            <img  :src="product.selectedImage" :alt="product.title" width="150px"   id="image"  class="ml-4">
            <hr>
            <label id="productsDetail"> <b> Ürün adı:</b> {{product.title}}</label>
            <label id="productsDetail"><b>Adet:</b> {{product.count}}</label>
            <label id="productsDetail"><b>Fiyat:</b> {{product.price}} TL</label>
        </app-product>
    </div>

</template>

<script>
import {eventBus} from '../main';

import Product from './product.vue';



export default {
    components : {
        appProduct : Product,
    },
    data() {
        return {
            productsList : [],
            info : "",
        }
    },
    created() {
            eventBus.$on("porductAdded" , (product) => {
                if (this.productsList.length < 10) {
                    this.productsList.push(product);
                    eventBus.$emit("progressBar" , this.productsList.length);
                }else{
                    this.info +="Daha fazla ürün ekleyemezsiniz!!!";
                }
                
                
            });
    }
}


</script>

