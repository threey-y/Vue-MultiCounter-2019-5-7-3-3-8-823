<template>
  <div class="counter">
    <span>{{index}}</span>
    <button v-on:click = "add">+</button>
    <span>{{ counter }}</span>
    <button v-on:click = "minus">-</button>
  </div>
</template>

<script>
export default {
  name: 'Counter',
  props: {
    index:Number,
    counter:Number
  },

  methods:{
    
    add:function(){
      this.counter++;
      this.deliver();
      },
    minus:function(){
      this.counter--;
      this.deliver();
    },
    deliver: function() {
      this.$emit("update", {
        index: this.index,
        value: this.counter
      });
    }
  } 
};
</script>