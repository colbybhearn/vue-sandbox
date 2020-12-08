<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
      </br>
      <div @click="directToggleP1">direct {{cp1}}</div></br>
      <div @click="commitToggleP1">commit {{cp1}}</div></br>
      <div @click="dispatchToggleP1">dispatch {{cp1}}</div></br>
      <div @click="resetOb">reset {{cob}}</div></br>
      <VisibilityToggle :value="cp1" text='toggle1' />
    </div>
    <router-view/>
  </div>
</template>

<script>

import Vue from 'vue'
import Vuex from 'vuex'
import { mapState } from 'vuex'

Vue.use(Vuex)

const store = new Vuex.Store({
  state: {
    ob:{
			p1:true,
			p2:false,
    },    
  },
  mutations: {
    toggleP1(state){
      state.ob.p1 = ! state.ob.p1;
    }    
  },
  actions: {
    actToggleP1(context){      
      context.commit('toggleP1');
    }
  }
})

import VisibilityToggle from './visibilityToggle.vue'

export default {
  name: 'App',
  store,  
  data: function(){
    return {
     
    }
  },
  computed:mapState({    
    cp1: state => state.ob.p1,
    cob: state => state.ob    
  }),  
  components: {    
  },
  watch:{
    
  },
  created: function(){
  },
  mounted: function(){      
  },
  methods: {
    directToggleP1(){
      this.$store.state.ob.p1=!this.$store.state.ob.p1;
    },
    commitToggleP1(){
      this.$store.commit('toggleP1');
    } ,   
    dispatchToggleP1(){
      this.$store.dispatch('actToggleP1');      
    },
    resetOb(){
      this.$store.state.ob={
        p1:true,
        p2:false
      }
    }
  },
  components:{
    VisibilityToggle
  }

}
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
