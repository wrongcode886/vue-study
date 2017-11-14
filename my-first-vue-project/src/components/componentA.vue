<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{msgfromfather}}</h2>
    <button v-on:click="onClickMe">Click!</button>
  </div>
</template>

<script>

export default {
  data () {
    return {
      msg: 'hello from component a!'

    }
  },
  
  props:['msgfromfather'],

  methods:{
    onClickMe:function(){
      console.log(this.msgfromfather)
    }
  }

}
</script>