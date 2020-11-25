<template>
  <div class="input-wrapper">
    <label>{{label}}</label>
    <input
      class="input"
      v-if="type==='input'"
      @input="customInput($event.target.value)"
      autocomplete="off"
      type="text"
    >
</template>
<script>
import { Validator } from "vee-validate";
const validator = new Validator();

data() {
    return {
      validationError: ""
    };
  },
  methods: {
    validate(value) {
      return validator.verify(value, this.validation, {
        name: this.label
      });
    },
    async customInput(value) {
      const { valid, errors } = await this.validate(value);
      if (valid) {
        this.validationError = "";
        this.$emit("input", value);
      } else {
        this.validationError = errors[0];
        this.$emit("input", "");
      }
    }
  }
  </script>