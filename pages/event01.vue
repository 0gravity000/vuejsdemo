<template>
  <section class="container">
    <router-link to="/">Go to Top</router-link>
    <hr>
    <h1>{{title}}</h1>
    <p>{{message}}</p>
    <hr>
    <button v-on:click="doAction">
    {{btn}}
    </button>
    <transition name="transit" 
        v-on:before-enter="startAction"
        v-on:before-leave="startAction"
        v-on:after-enter="endAction" 
        v-on:after-leave="endAction">
      <p v-if="flg" class="trans">Transition! ボタンを押すと、イベントが発生する</p>
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
      title:'transition01',
      message: 'イベントのサンプル01',
      flg:true,
      btn:'Hide',
    };
  },
  methods:{
    doAction: function(){
      this.flg = !this.flg;
    },
    startAction: function(){
      if (this.flg){
        this.message = '現れます……';
      } else {
        this.message = '消えます……';
      }
    },
    endAction: function(){
      if (this.flg){
        this.btn = 'Hide';
        this.message = '現れました。';
      } else {
        this.btn = 'Show';
        this.message = '消えました。';
      }
    }
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
  background-color: #ddf;
  padding:10px;
  font-size:20pt;
}
.transit-enter-active {
  transition: opacity 0.5s;
}
.transit-leave-active {
  transition: opacity 3.0s;
}
.transit-enter {
  opacity: 0;
}
.transit-enter-to {
  opacity: 1.0;
}
.transit-leave {
  opacity: 1.0;
}
.transit-leave-to {
  opacity: 0;
}

</style>
