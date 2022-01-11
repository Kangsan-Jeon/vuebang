<template>

  <div class="black-bg" v-if="modalIsOpen == true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
      <button @click="modalIsOpen=false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ i+1 }}. {{ menu }}</a> <!-- key: 반복문 돌린 요소를 컴퓨터가 구분하기 위해 씀, 변수 정의 역할 -->
  </div>


  <div v-for="(product, i) in products" :key="i">
    <img :src=product.image class="room-img" @click="modalIsOpen=true"/>
    <h4 @click="modalIsOpen=true">{{ product["title"] }}</h4>
    <p>{{ product["price"] }}원</p>
    <!-- v-on = @, event example: mouseover, drag, ... -->
    <button @click="reportClick(product)">허위매물신고</button> <span>신고수: {{ product['reportCnt'] }}</span>
  </div>

</template>

<script>
import onerooms from './assets/oneroom.json';

export default {
  name: 'App',
  data() {
    // 자주 변경되는 값을 data에 저장 -> 사이트 이름은 data에 저장안해도 됨
    const products = onerooms.map(oneroom => {
        return {...oneroom, reportCnt: 0}
      })    
    return {
      products: products,
      // products: [
      //   {
      //     name: "역삼동 원룸",
      //     price: "50만원",
      //     reportCnt: 0,
      //     imgPath: require("./assets/room0.jpg"),
      //   },
      //   {
      //     name: "천호동 원룸",
      //     price: "60만원",
      //     reportCnt: 0,
      //     imgPath: require("./assets/room1.jpg"),
          
      //   },
      //   {
      //     name: "마포구 원룸",
      //     price: "70만원",
      //     reportCnt: 0,
      //     imgPath: require("./assets/room2.jpg"),
      //   },
      // ],
      menus: ['Home', 'Shop', 'About'],
      modalIsOpen: false,
    }
  },
  methods: {
    reportClick(product) {
      product['reportCnt']++
    },
  },
  components: {
  }
}
</script>

<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}
</style>
