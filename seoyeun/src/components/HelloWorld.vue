<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank" rel="noopener">eslint</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
    <ul ref="ul">
      <li v-for="loop in loopi" :key="loop" @click="onClick($event,'hello')" class="clickable" @mouseover="onMouseover">
        {{loop}}
      </li>
      <h3>{{num}}</h3>
      <input type="text" v-model="num">
    </ul>
  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  props: {
    msg:Boolean
  },
  data(){
    return{
      loopi:['m','u','n'],
      num:0 //초기화 값
      }
  },
  methods: {
    onClick (e,msg){ //onClick : function onClick(){} 에서 이렇게 줄여서 사용 가능
      console.log(msg+"You clicked " +e) //화살표 함수는 사용 불가
    }, 
    onMouseover(e){
      console.log(e) //이게 왜,,,, onClick에서 주지도 않았
    }
  },
  beforeCreate(){
    console.log(this.num,"undefined yet")
  },

  beforeMount(){
    console.log(this.num,"finally defined but still component is not mounetd",this.$refs.ul)
  },
  mounted(){
    console.log("mounted")
  },
  beforeUnmount() {
    console.log("will unmount")
  },
  //before update는 Update되기 전 상태를 말함(snapshot을 찍는 것처럼)
  //before -- 은 모두.
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.clickable{
  cursor: pointer;
}
.active{
  color: red;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
