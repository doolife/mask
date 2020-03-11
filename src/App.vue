<template>
  <div id="app">
    <div>{{nowTime}}</div>
    <Store />
  </div>
</template>

<script>
import Store from './components/Store';
export default {
  name:'app',
  components:{
    Store
  },
  computed: {
    titleComputed() {
      console.log('I change when this.property changes.')
      return this.property
    }
  },
  data(){
    return {
      nowTime:0
    }
  },
  mounted() {
    console.log("mounted")
    this.titleComputed
  },
  beforeCreate(){
    console.log("beforeCreate")
  },
  created(){
    console.log("created")
    // this.nowTime = (new Date()).getTime();
  },
  beforeUpdate(){
    console.log("beforeUpdate")
  },
  updated(){
    console.log("updated")
  },
  beforeMount(){
    console.log("beforeMount")
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
