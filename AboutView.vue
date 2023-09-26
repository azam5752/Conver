<template>
  <div class="money">
    <Money />
  </div>
</template>

<script>
// @ is an alias to /src
import Money from "@/components/Money.vue";
export default {
  name: "HomeView",
  components: {
    Money,
  },
};
</script>
