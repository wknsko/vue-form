<template>
  <div class="form-control" :class="{ invalid: errors }">
    <label :for="id">{{ label }}</label>
    <input type="text"  :id="id" :placeholder="placeholder"
    :value="value" @input="change">
    <small v-if="errors">{{ errors }}</small>
  </div>
</template>

<script>
  export default {
    emits: ['update:value'],
    props: {
      value: String,
      placeholder: String,
      label: String,
      errors: String
    },
    data() {
      return {
        id: 'input-' + Math.random()
      }
    }, methods: {
      change() {
        this.$emit('update:value', event.target.value);
      }
    }

  }
</script>

<style scoped>

</style>
