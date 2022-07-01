<template>

  <div class="black-bg" v-if="모달창열렸니 === true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세내용</p>
    </div>
    <button @click="모달창열렸니 = false">닫기</button>
  </div>

  <div class="menu">
    <!-- <a v-for="작명 in 반복횟수" :key="작명">Home</a> -->
    <a v-for="(a,i) in 메뉴들" :key="(a,i)">{{ a }}</a>
  </div>

  <div>
    <img class="room-img" :src="원룸들[0].image" />
    <h4>{{원룸들[0].title}}</h4>
    <P>{{원룸들[0].price}} 원</P>
  </div>
</template>

<script>
import data from './assets/oneroom.js'
export default {
  name: 'App',
  data() {
    return{
      원룸들 : data,
      모달창열렸니 : false,
      신고수 : [0,0,0],
      메뉴들: ['Home', 'Shop', 'About'],
      products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },
  methods: {
    increase(){
      this.신고수 += 1
    }
  },
  components: {
  }
}
</script>

<style>
body{
  margin: 0
}
div{
  box-sizing: border-box;
}
.black-bg{
  width:100%; height:100%;
  background:rgba(0,0,0,.5);
  position: fixed; padding:20px;
}
.white-bg{
  width:100%; background:#fff;
  border-radius: 8px;
  padding:20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu{
  background:darkslateblue;
  padding:15px;
  border-radius: 5px;
}
.menu a{
  color:#fff;
  padding:10px;
}
.room-img{
  width:100%;
  margin-top:40px;
}
</style>
