<template>
  <div>
    <currency-input v-model="innerValue" ref="currencyInput" />
  </div>
</template>

<script>
import CurrencyInput from "@/currency-input.vue";
export default {
  components: {
    CurrencyInput,
  },
  props: ["value"],
  data() {
    return {
      innerValue: null,
    };
  },
  watch: {
    innerValue(newVal) {
      this.$emit("input", newVal);
    },
  },
  created() {
    this.innerValue = this.value;
  },
};
</script>

<style></style>
