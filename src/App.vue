<template>
  <div id="app">
    <ul class="store">
      <template v-for="(store, index) in maskList.listArr">
        <li class="store__list" :key="store.list">{{index}}<br />{{store.name}}<br />{{store.addr}}</li>
      </template>
    </ul>
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
      maskList:{
        listArr:[]
      }
    }
  },
  methods:{
    resultArr(){
      console.log(this.maskList.listArr.addr)
    }
    // this.titleComputed
  },
  beforeCreate(){
    console.log("beforeCreate")
  },
  created(){
    console.log("created")
  },
  beforeMount(){
    console.log("beforeMount")
    fetch('https://8oi9s0nnth.apigw.ntruss.com/corona19-masks/v1/stores/json')
    .then((response) => {
      if(response.ok){
        return response.json();
      }
      throw new Error('Network response was not ok');
    })  
    .then((json) => {
      console.log(json)
      json.storeInfos.forEach((str) => {
          this.maskList.listArr.push(str)
      });
    })  
    .catch((error) => {
      console.log(error, 'error')
    })
  }
};
</script>

<style>
@charset "utf-8";

/* LDN 2017-02-08 */

/* reset */
html, body, div, span, object, iframe, h1, h2, h3, h4, h5, h6, p, button, blockquote, a, address, img, strong, dl, dt, dd, ol, ul, li, fieldset, form, pre, label, legend, table, caption, tbody, tfoot, thead, tr, th, td, input
{margin:0; padding:0; font-weight:normal; font-size:100%;}

/* HTML5 display-role reset for older browsers */
article, aside, canvas, details, figcaption, figure, footer, header, hgroup, nav, menu, nav, section, video {margin:0; padding:0; display:block;}

html, body {width:100%; height:100%;}
html {overflow-y:scroll;}
body, input, button, textarea, select {font-family:"Malgun Gothic", "맑은 고딕", Dotum, "돋움", Gulim, "굴림", Verdana, tahoma, Sans-serif; font-size:12px; color:#4c4c4c; line-height:1.2;}
input, select, button{vertical-align:middle}
li {list-style:none}
img {margin:0; padding:0; vertical-align:top; border:none; /*max-width:100%;*/}
fieldset, iframe{border:none;}
textarea {resize:none;}
legend {display:none;}
button {margin:0; padding:0; border:0; cursor:pointer; background:transparent;}
table {border-spacing:0; border-collapse:collapse;}
caption, th, td {text-align:left;}
em, address{font-style:normal;}
label {cursor:pointer;}
/*object {outline:none;}*/

/* cross */
.input_check,.input_radio {width:13px; height:13px; margin:-1px; vertical-align:top;}

/* a */
a {color:#4c4c4c; text-decoration:none;} /* 파폭 및 익스 링크 점선없애기 outline:none; selector-dummy: expression(this.hideFocus=true); */
a:hover {color:#4c4c4c; text-decoration:underline;}

#app {
  text-align:center;
}
.store {
  
}
.store__list {
  margin-top:20px;
  padding:10px;
  font-size:14px;
  border:1px solid #ddd;
}
.store__list:first-child {
  margin-top:0;
}
</style>
