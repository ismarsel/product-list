<template>
    <select 
      v-model="value"
      @change="changeValue">>
      <option
        v-for="option in options"
        :key="option.value" 
        :value="option.value">
        {{ option.text }}
      </option>
  </select>
</template>

<script>
export default {
  data() {
      return {
      value: '',
      }
    },
    props: {
      options: {
        type: Array,
        default () {
           return []
          }
      }
    },
    methods: {
      changeValue () {
        this.$emit('changeValue', this.value)
      }
    }
  }
</script>

<style>

</style>