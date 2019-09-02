<template>
  <div id="app">
    <input type="text" class="form-control" v-model="num" v-on:input="initalMessage()">
    <counter 
    v-for="n in parseInt(num)" 
    v-bind:key="n" 
    v-bind:index="n"
    v-on:update="updateNumber"
    v-bind:counter="message[n-1]"/>
    <p>{{sum}}</p>  
  </div>
</template>

<script>

import Counter from './components/Counter.vue'

export default {
  name: 'app',
  components: {
    Counter
  },
  data:function(){
    return{
      num:0,
      message: [],
      sum:0
    };
  },
  methods:{
    initalMessage: function() {
      let size = parseInt(this.num);
      if (size == 0) {
        this.message = [];
      } else {
        this.message = new Array(size);
        for (let i = 0; i < this.message.length; i++) {
          this.message[i] = i + 1;
        }
      }
      this.getsum();
    },
    updateNumber: function(data) {
      this.message[data.index - 1] = data.value;
      this.getsum();
    },
    getsum: function() {
      this.sum = 0;
      for (var i = 0; i < this.message.length; i++) {
        this.sum += this.message[i];
      }
    }
  }
};
</script>