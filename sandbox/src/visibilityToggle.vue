<template>
    <div class='viewOpt' v-on:click="toggle">
        visToggle
        <div v-if="cVis" style='padding:0 1px 0 1px;'>{{cVis}}</div>
        <div v-if="!cVis">{{cVis}}</div>
        <label style='display:inline;padding-left: 5px'>{{text}}</label>
    </div>
</template>

<script>
export default {
  props: ['value', 'text'],
  data: function(){
      return {
          visible: this.value
      };
  },
  computed:{
      cVis(){
          return this.$store.state.ob['p1'];
      }
  },
  methods: {
      toggle: function(){
          this.visible=!this.visible;

          //this.$emit('toggle');
          //this.$emit('input', this.visible)
          this.$store.dispatch("actToggleP1");
      }
  }
}
</script> 

<style scoped>



</style>


