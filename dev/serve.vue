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
    innerValue3: null,
  }),
});
</script>

<template>
  <div id="app">
    <In v-model="innerValue2"></In>

    <In v-model="innerValue3"></In>

    WTF

    {{ innerValue2 }}
    {{ innerValue3 }}

    <hr />
  </div>
</template>
