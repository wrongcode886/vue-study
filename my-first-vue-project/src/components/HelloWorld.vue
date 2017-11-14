<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2 v-text="title"></h2>
    <input v-model="newItem" v-on:keyup.enter="addNew">
    <ul>
      <li v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinish(item)">{{item.label}}</li>
    </ul>
    <component-a msgfromfather="youdie"></component-a> 
  </div>
</template>

<script>
import store from './storage'
import componentA from './componentA'
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',

      title:'this is a todo list',

      items:store.fetch(),
      newItem:''
    }
  },
components:{componentA},
  watch:{
    items:{
      handler:function(items){
        store.save(items)
      },
      deep:true
    }
  },

  methods:{
      toggleFinish:function(item){
        item.isFinished =!item.isFinished 
      },
      addNew:function(){
        this.items.push({
          label:this.newItem,
          isFinished:false
        })
        this.newItem=''
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.finished{
  text-decoration: underline;
}
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  /*display: inline-block;*/
  margin: 0 10px;
 cursor: pointer;
}
a {
  color: #42b983;
}
</style>
