<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <Calculator msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import Calculator from "@/components/Calculator.vue";
export default {
  name: "HomeView",
  components: {
    Calculator,
  },
};
</script>
