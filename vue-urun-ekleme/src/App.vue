<template>
  <div class="container">
    <h1 style="color:white; text-align:center;" class="mt-1">Ürün Ekleme</h1>
    <appNewProduct></appNewProduct>

    <app-progress></app-progress>
    <app-products></app-products>
  </div>
</template>

<script>
import NewProduct from './components/NewProduct';
import Products from './components/products.vue';
import Progress from './components/progress.vue'
export default {
  components :{
    appNewProduct : NewProduct,
    appProducts : Products,
    appProgress : Progress,
  }
}
</script>

<style >
body{
  background-color: rgb(17, 10, 29);
}
.col{
  border-radius: 10px;
  background-color:  grey;
  margin: 5px;
  opacity: .8;
  transition:  .5s;

}
.col:hover{
  opacity:1 ;
  transition:  .5s;

}
.imgscreen{
  border-right: 1px solid grey;
  border-left: 1px solid grey;
  height: 300px;

}
#lbl{
  align-content: center;
  justify-content: center;
  display: flex;
  font-size: 20px;
  margin-top:10px ;
}
#img{
  margin-left: 180px;
  width: 200px;

}


.products{
  margin-top: 20px;
  height: auto;
  background-color: rgb(148, 151, 151);
  border-radius: 10px;
  opacity: .8;
  min-height: 300px;
}
.products:hover{
  opacity: 1;
  transition:  .5s;
}
.product{
  display: inline-block;
  flex-wrap: wrap;  
  margin: 20px;
  height: 300px;
  width: 200px;
  background-color: rgb(44, 44, 43);
  color: white;
  border-radius: 5px;
  transition: 1s;
}
.product:hover{
  cursor: pointer;
  transform:translate(0px,-30px);
  transition: 1s;
}
#productsDetail{
  padding: 2px;
  margin-top: 5px;
  margin-left: 10px;
}



</style>
