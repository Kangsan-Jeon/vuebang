<template>

  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ i+1 }}. {{ menu }}</a> <!-- key: 반복문 돌린 요소를 컴퓨터가 구분하기 위해 씀, 변수 정의 역할 -->
  </div>

  
  <div v-for="(product, i) in products" :key="i">
    <h4>{{ product["name"] }}</h4>
    <p>{{ product["price"] }}</p>
    <!-- v-on = @, event example: mouseover, drag, ... -->
    <button @click="reportClick(product)">허위매물신고</button> <span>신고수: {{ product['reportCnt'] }}</span>
  </div>

</template>

<script>

export default {
  name: 'App',
  data() {
    // 자주 변경되는 값을 data에 저장 -> 사이트 이름은 data에 저장안해도 됨
    return {
      products: [
        {
          name: "역삼동 원룸",
          price: "50만원",
          reportCnt: 0,
        },
        {
          name: "천호동 원룸",
          price: "60만원",
          reportCnt: 0,
        },
        {
          name: "마포구 원룸",
          price: "70만원",
          reportCnt: 0,
        },
      ],
      menus: ['Home', 'Shop', 'About'],
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
