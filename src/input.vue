<template>
  <CurrencyInput
    v-model="innerValue"
    v-bind="$attrs"
    :valid="valid"
    :required="required"
    :id="inputId"
    class="form-control"
  />
</template>
<script>
import CurrencyInput from "vue2-currency-input";
export default {
  inheritAttrs: false,
  components: { CurrencyInput },
  name: "base-input",
  props: {},
  data() {
    return {
      innerValue: null,
    };
  },
  mounted() {
    this.innerValue = this.value;
  },
  watch: {
    value(val) {
      this.innerValue = val;
    },
    innerValue(val) {
      this.$emit("input", val);
    },
  },
};
</script>
<style></style>
