<template>
  <input
    type="text"
    @input="formatCurrency"
    @blur="formatCurrency"
    v-bind="$attrs"
    v-model="innerValue"
  />
</template>

<script>
export default {
  name: "CurrencyInput",
  props: {
    value: null,
    setNewValue: null,
  },
  data: () => ({
    innerValue: null,
  }),
  created() {
    if (this.value == "" || this.value == 0) {
      this.innerValue = null;
      return;
    } else {
      this.innerValue = this.doFormat(this.value, "blur");
    }
  },
  watch: {
    // I have to do this because I emit a float and the format would be wrong otherwise
    setNewValue(newVal) {
      this.setNewValue = newVal;
      this.innerValue = this.doFormat(newVal, "blur");
    },
    innerValue(newVal) {
      if (newVal == null || newVal === "") this.$emit("input", 0);
      else this.$emit("input", parseFloat(newVal.replace(/,/g, "")));
    },
  },
  methods: {
    //picked this up from https://codepen.io/559wade/pen/LRzEjj
    formatNumber(n) {
      // format number 1000000 to 1,234,567
      return n.replace(/\D/g, "").replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
    doFormat(input_val, type) {
      if (input_val == null || input_val == undefined) return;

      input_val = input_val.toString();
      if (input_val.indexOf(".") >= 0) {
        // get position of first decimal
        // this prevents multiple decimals from
        // being entered
        var decimal_pos = input_val.indexOf(".");

        // split number by decimal point
        /* eslint-disable no-unused-vars */
        var ls = input_val.substring(0, decimal_pos);
        /* eslint-disable no-unused-vars */
        var right_side = input_val.substring(decimal_pos);

        // add commas to left side of number
        ls = this.formatNumber(ls);

        // validate right side
        right_side = this.formatNumber(right_side);

        // On blur make sure 2 numbers after decimal
        if (type === "blur") {
          right_side += "00";
        }

        // Limit decimal to only 2 digits
        right_side = right_side.substring(0, 2);

        input_val = ls + "." + right_side;
        console.log(input_val);
      } else {
        input_val = this.formatNumber(input_val);
        // final formatting
        if (type === "blur") {
          input_val += ".00";
        }
      }

      return input_val;
    },
    formatCurrency(input) {
      const type = input.type;

      var input_val = this.innerValue;
      if (input_val === "") {
        return;
      }

      var original_len = input_val.length;
      var caret_pos = input.srcElement.selectionStart;

      input_val = this.doFormat(input_val, type);
      this.innerValue = input_val;

      this.$nextTick(() => {
        if (type != "blur") {
          //safari didnt like this
          var updated_len = input_val.length;
          caret_pos = updated_len - original_len + caret_pos;
          input.srcElement.setSelectionRange(caret_pos, caret_pos);
        }
      });
    },
  },
};
</script>
