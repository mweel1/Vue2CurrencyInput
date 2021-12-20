<script>
import Vue from "vue";
import CurrencyInput from "@/currency-input.vue";
import In from "./in.vue";
export default Vue.extend({
  name: "ServeDev",
  components: {
    CurrencyInput,
    In,
  },
  data: () => ({
    innerValue2: null,
  }),
});
</script>

<template>
  <div id="app">
    <In v-model="innerValue2"></In>
    {{ innerValue2 }}

    <hr />
  </div>
</template>
