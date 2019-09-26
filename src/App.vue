<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <WaterFall :water-wrap-width="1200" :block-width="393" :gap="10" :wrap-list="wrapList"/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import WaterFall from './components/waterFall.vue'

export default {
  name: 'app',
  components: {
    // HelloWorld,
    WaterFall,

  },
  data(){
    return{
      wrapList:[
        {url:require('./assets/1.jpg'),text:"pic1"},
            {url:require('./assets/2.jpg'),text:"pic2"},
            {url:require('./assets/3.jpg'),text:"pic3"},
            {url:require('./assets/4.jpg'),text:"pic4"},
            {url:require('./assets/5.jpg'),text:"pic5"},
            {url:require('./assets/6.jpg'),text:"pic6"},
            {url:require('./assets/7.png'),text:"pic7"},
            {url:require('./assets/8.jpeg'),text:"pic8"},
            {url:require('./assets/9.png'),text:"pic9"},
            {url:require('./assets/10.png'),text:"pic10"},
            {url:require('./assets/11.png'),text:"pic11"},
            {url:require('./assets/12.png'),text:"pic12"},
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
