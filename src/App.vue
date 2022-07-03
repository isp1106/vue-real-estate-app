<template>
  <div class="container">

    <transition name="fade">
      <ModalRoom @closeModal="모달창열렸니 = false" :누른거="누른거" :모달창열렸니="모달창열렸니" :원룸들="원룸들" />
    </transition>

    <div class="menu">
      <!-- <a v-for="작명 in 반복횟수" :key="작명">Home</a> -->
      <a v-for="a in 메뉴들" :key="a">{{a}}</a>
    </div>

    <DiscountInfo :amount="amount" />
    <div class="ui-align">
      <button class="btn-align" @click="priceSort">가격순정렬</button>
    </div>
    <CardBox @openModal="모달창열렸니 = true; 누른거 = $event" :원룸="원룸들[i]" v-for="(a, i) in 원룸들" :key="a" />
  </div>
</template>

<script>
import data from './assets/oneroom.js';
import DiscountInfo from './DiscountInfo.vue';
import ModalRoom from './ModalRoom.vue';
import CardBox from './CardBox.vue';
export default {
  data(){
    return{
      누른거:0,
      메뉴들:['Home', 'About', 'Shop'],
      원룸들: data,
      모달창열렸니 : false,
      amount : 30
    }
  },
  methods:{
    priceSort() {
      this.원룸들.sort(function(a,b){
        return a.price - b.price
      })
    }
  },
   mounted () {
    setInterval(() => {
      if(this.amount <= 0){
        clearInterval();
      }
      else{
        this.amount--;
      }
    }, 1000);
   },
  components:{
    DiscountInfo,
    ModalRoom,
    CardBox,
  }
}
</script>

<style>
  .ui-align{text-align: right;margin:20px 0;}
  .btn-align{border:none; background:darkslateblue; color:#fff; width:100px; height:40px; border-radius: 10px;}
  .fade-enter-from {opacity: 0;}
  .fade-enter-active {transition: all 1s;}
  .fade-leave-from {opacity: 1;}
  .fade-leave-active {transition: all 1s;}
  .fade-leave-to {opacity: 0;}
  *{box-sizing: border-box;}
  .body{margin:0; text-align:center}
  .container{text-align:center;}
  .menu{border-radius:10px; background:darkslateblue;
   color:#fff; text-align: center; padding:10px;}
  .menu a{padding:10px;}
  img{width:100%;}
.modal{
  width:100%; height:100%;
  background:rgba(0,0,0,.5);
  position: fixed; padding:20px;
}
.modal .in{
  width:90%; background:#fff;
  border-radius: 8px;
  padding:20px;
  position:absolute;
  top:50%;
  left:50%;
  transform: translate(-50%, -50%);
}
.btn-close{
  background:darkslateblue;
  color:#fff;
  border:none;
  border-radius: 10px;
  width:150px;
  height:40px;
}

</style>