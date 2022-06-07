<template>
  <div id="app">
  <h1>{{ input.value }}</h1>
    <div :class="{ shake: disabled }">
      <button @click="warnDisabled">Click me</button>
      <span v-if="disabled">This feature is disabled!</span>
    </div>
  </div>
</template>

<script>

import { ref } from 'vue';
export default {
  
  data() {
    const input = ref([]);
    return {
      disabled: false,
      input,
    }
  },
  created() {
    const getInput = this.input.value;
    console.log({getInput});
    this.alertText();
  },
  methods: {
    warnDisabled() {
      this.disabled = true;
      this.input.value = "Loading";
      setTimeout(() => {
        this.disabled = false;
        this.input.value = "Closed";
      }, 1500)
    },
    alertText() {
      this.input.value = "Hello From Vue";
    }
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
  margin-top: 60px;
}
.shake {
  animation: shake 0.82s cubic-bezier(0.36, 0.07, 0.19, 0.97) both;
  transform: translate3d(0, 0, 0);
}

@keyframes shake {
  10%,
  90% {
    transform: translate3d(-1px, 0, 0);
  }

  20%,
  80% {
    transform: translate3d(2px, 0, 0);
  }

  30%,
  50%,
  70% {
    transform: translate3d(-4px, 0, 0);
  }

  40%,
  60% {
    transform: translate3d(4px, 0, 0);
  }
}
</style>
