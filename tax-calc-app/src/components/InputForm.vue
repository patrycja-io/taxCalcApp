<template>
  <form @submit.prevent="handleSubmit">
    <Input
      type="input"
      label="Gross Salary"
      validation="required|numeric"
      v-model="inputs.incomeValue"
      @input="input"
    />
    <Input
      type="dropdown"
      label="Year"
      validation="required"
      :options="options.year"
      v-model="inputs.year"
    />

    <button
      class='submit-btn'
      :disabled="!isEnabled"
      type="submit"
    >
      Calculate!
    </button>
  </form>
</template>

<script>
import Input from "./Input";
export default {
  name: "InputForm",
  components: {
    Input
  },
  data() {
    return {
      inputs: {
        incomeValue: "",
        year: "",
      },
        year: [{ label: "2018", value: "2018" }],
      }
    }
  }
 computed: {
    isEnabled: function() {
      return !!Object.values(this.inputs).every(Boolean);
    }
  }
  methods: {
    input: function(input) {
      if (input.type === "input") {
        this.incomeValue = input.value;
      }
    }
    handleSubmit: function() {
      const { isInChurch, stateOfResidence, year } = this.inputs;
      const inputValues = {
        ...this.inputs,
        year: year.value,
        isInChurch: isInChurch.value,
        stateOfResidence: stateOfResidence.value
      };
      this.$emit("submitted", inputValues);
    }
  }
};

</script>

<style lang="scss" src="../assets/styles/InputForm.scss"/>
