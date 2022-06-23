<template>
  <select
      name=""
      id=""
      v-model="modelValue"
      @change="changeOption"
  >
    <option disabled value="">По умолчанию</option>
    <option
        v-for="option in options"
        :key="option.value"
        :value="option.value"
    >
      {{option.name}}
    </option>
  </select>
</template>

<script>
export default {
  name: 'SelectCustom',
  props: {
    modelValue: {
      type: String,
    },
    options: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    changeOption(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style scoped lang="sass">
select
  border: none
  background: #FFFEFB
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1)
  border-radius: 4px
  padding: 10px 16px
  font-size: 12px
  line-height: 15px
  color: #B4B4B4
  box-sizing: border-box
  width: 151px
  -webkit-appearance: none
  -moz-appearance: none
  appearance: none

</style>