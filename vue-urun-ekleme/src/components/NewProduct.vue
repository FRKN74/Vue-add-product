<template>
    <div class="row mt-5">

        <div class="col md-2">
            <label id="lbl">İmage</label>
            <hr><img :src="product.selectedImage == null ? 'src/assets/default.png' : product.selectedImage" alt="Resim yok" id="img" class="img-responsive text-center mb-3" >
            <br>
            <input type="file" ref="file" style="display:none;" class="form-control" @change="onChange($event)">
            <button type="button" class="btn btn-outline-warning float-right " @click="$refs.file.click()">Resim seç</button>
        </div>

        <div class="col md-10">
            <label id="lbl">Kayıt giriş</label>
            <hr>
            <div class="row ml-5">
                <div class="form-group">
                    <label for="">Ürün Adı: </label>
                    <input type="text" name="" v-model="product.title"  class="form-control">
                </div>
            </div>
            <div class="row ml-5">
                <div class="form-group">
                    <label for="">Ürün Adeti: </label>
                    <input type="number" name="" v-model="product.count"  class="form-control">
                </div>
            </div>
            <div class="row ml-5">
                <div class="form-group">
                    <label for="">Ürün Fiyatı: </label>
                    <input type="text" name="" v-model="product.price"  class="form-control">
                </div>
            </div>
            <div class="row">
                <div class="btn-group">
                    <button @click="addProduct" class="btn btn-success mb-2 ml-5 " >Ürün Ekle</button>
                </div>
            </div>
        </div>
        

    </div>    
</template>

<style>

</style>

<script>

import {eventBus} from '../main'

export default {
    data() {
        return {
            product: {
                title : null,
                count: null,
                price:null,
                selectedImage : null,
                totalPrice:  null,

            }
        }
    },
    methods: {
        onChange(e){
            const file = e.target.files[0];  //birden fazla dosya seçmemeiz hallinde array olarak gelir ve 0 indexli elemanı alır.
            this.product.selectedImage = URL.createObjectURL(file); // dosya uzantısı.
        },
        addProduct(){
            this.product.totolPrice = this.product.count * this.product.price;
            eventBus.$emit("porductAdded",this.product);
            this.product ={

                title :null,
                count : null,
                price : null,
                totolPrice:null,
                selectedImage: null,
            }
        }
    },
}
</script>