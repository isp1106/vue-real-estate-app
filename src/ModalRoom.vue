<template>
  <div class="modal" v-if="모달창열렸니 === true">
    <div class="in">
      <h4>{{원룸들[누른거].title}}</h4>
      <img :src="원룸들[누른거].image" />
      <p>{{원룸들[누른거].content}}</p>
      <input v-model.number="month">
      <p>{{month}}개월 선택함 : {{원룸들[누른거].price * month}} 원</p>
      <DiscountInfo />
      <button @click="모달창열렸니 = false" class="btn-close">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalRoom',
  data(){
    return {
      month: 1,
    }
  },
  beforeUpdate(){
    if(this.month < 3){
      alert('계약기간이 너무적음 최소3달')
      this.month = 3
    }
  },
  watch : {
    month(a){
      if (isNaN(a) == true || a >= 13){
        alert('문자입력하지마라');
        this.month = 1;
      }
    },
  },
  props : {
    원룸들 : Array,
    누른거 : Number,
    모달창열렸니 : Boolean
  },
  methods:{
    closeModal(){
      $this.emit('closeModal', this.모달창열렸니)
    }
  }
}
</script>

<style>
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