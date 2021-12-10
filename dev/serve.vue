<script>
import Vue from "vue";
import CurrencyInput from "@/currency-input.vue";

export default Vue.extend({
  name: "ServeDev",
  components: {
    CurrencyInput,
  },
  data: () => ({
    innerValue: 12,
  }),
});
</script>

<template>
  <div id="app">
    <currency-input v-model="innerValue" />
    {{ innerValue }}
  </div>
</template>
