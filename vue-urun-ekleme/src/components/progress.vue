<template>
    <div class="loadingBar">
        <div class="loading"  style="width: 10%;" :style="{width : progress + '%'}"  >{{ currentItem }}/10 asda</div>
    </div>
</template>

<script>
import {eventBus} from '../main';
export default {
    data() {
        return {
            currentItem : 0,
            progress : 0,
        }
    },
    created() {
        eventBus.$on("progressBar" , (productListCount) => {
            this.currentItem = productListCount;
            this.progress = productListCount*10;
        })
    },
}
</script>

<style scoped >
    .loadingBar{
margin-top: 20px;
background-color: blanchedalmond;
height: 20px;
border-radius: 5px;
}
.loading{
height: 20px;
background-color: rgb(0, 132, 255);
border-radius: 5px;
text-align: center;
color: wheat;
transition: 1s;
}
</style>