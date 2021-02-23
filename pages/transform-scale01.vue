<template>
  <section class="container">
    <router-link to="/">Go to Top</router-link>
    <hr>
    <h1>{{title}}</h1>
    <p>{{message}}</p>
    <hr>
    <button v-on:click="doAction">
    Show/Hide
    </button>
    <br><br>
    <transition name="transit">
      <p v-if="flg" class="trans">Transform!</p>
    </transition>
  </section>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    title:String,
  },
  data: function(){
    return {
      title:'transform01',
      message: 'トランスフォーム(scale)のサンプル01',
      flg:true,
      btn:'Hide',
    };
  },
  methods:{
    doAction: function(){
      this.flg = !this.flg;
    },
  },
}
</script>

<style>
.container {
  padding:5px 10px;
}
h1 {
  font-size: 60pt;
  color: #345980;
}
p {
  padding-top:5px;
  font-size: 20pt;
}
a {
  font-size:16pt;
}

.trans {
  width: 150px;
  background-color: #ddf;
  padding:10px;
  font-size:20pt;
}
.transit-enter-active {
  transition: 1.0s;
}
.transit-leave-active {
  transition: 1.0s;
}
.transit-enter, .transit-leave-to {
  transform: scale(5.0);
  opacity: 0.1;
}

</style>
