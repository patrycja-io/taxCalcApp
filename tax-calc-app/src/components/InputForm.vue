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
export default {
  name: 'InputForm'
}
</script>

<style lang="scss" src="../assets/styles/InputForm.scss"/>