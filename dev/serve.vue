<script>
import Vue from "vue";
import CurrencyInput from "@/currency-input.vue";

export default Vue.extend({
  name: "ServeDev",
  components: {
    CurrencyInput,
  },
  data: () => ({
    innerValue: 123223.1,
    innerValue2: 12.1,
  }),
});
</script>

<template>
  <div id="app">
    <currency-input v-model="innerValue" />
    {{ innerValue }}
    <hr />
  </div>
</template>
