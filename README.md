# Vue 2 Currency Input

Vue 2.x input component that formats numbers into USD currency as the user types.

  <a href="https://www.npmjs.com/package/bootstrap-vue">
    <img src="https://flat.badgen.net/npm/v/vue2-currency-input" alt="Current version">
  </a>

  <a href="https://vuejs.org">
    <img src="https://flat.badgen.net/badge/vue.js/2.6.x/4fc08d" alt="Vue.js version">
  </a>

## Demo

![demo](https://user-images.githubusercontent.com/77025147/145624983-e0f56048-2faf-40e0-a2ca-7a7dc19012a8.gif)

## Install

```
npm install vue2-currency-input --save
```

## Usage

```
<script>
import Vue from 'vue';
import CurrencyInput from "vue2-currency-input";

export default Vue.extend({
  name: 'ServeDev',
  components: {
    CurrencyInput
  }
});
</script>

<template>
  <div id="app">
    <currency-input />
  </div>
</template>
```

## Additional Notes

This component only formats to US currency.

It will take a string or number and always returns a float

If the string is empty a 0.00 will be returned

Released under the MIT [License](./LICENSE).
