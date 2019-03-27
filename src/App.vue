<template>
  <div>
    <app-header></app-header>
    <transition name="fade" appear>
      <component :is="quiz" @result="result" :total="total"></component>
    </transition>
  </div>
</template>

<script>
import Header from "./Header.vue";
import Panel from "./Panel.vue";
import Result from "./Result.vue";

export default {
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      quiz: 'app-panel',
      total: 0
    }
  },
  methods: {
    result(result, total) {
      this.total = (result)?total:false;
      this.quiz = 'app-result';
      setTimeout(function(){
        this.quiz = 'app-panel';
      },10);
    }
  },
  components: {
    'app-header': Header,
    'app-panel': Panel,
    'app-result': Result
  }
}
</script>

<style lang="scss">
  .fade-enter-active, .fade-leave-active {
    transition: all 0.5s ease-out;
    rotate: 60deg;
  }

  .fade-enter, .fade-leave-to {
      opacity: 0;
      rotate: 0;
  }
</style>
