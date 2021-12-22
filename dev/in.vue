<template>
  <div>
    <currency-input v-model="innerValue" ref="currencyInput" />

    <button @click="$refs.currencyInput.forceValue(950.12)">100</button>
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
