<template>
  <div>
    <app-header></app-header>
    <app-panel></app-panel>
  </div>
</template>

<script>
import Header from "./Header.vue";
import Panel from "./Panel.vue";

export default {
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  components: {
    'app-header': Header,
    'app-panel': Panel
  }
}
</script>

<style lang="scss">

</style>
