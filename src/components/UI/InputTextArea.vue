<template>
  <textarea
      :value="modelValue"
      @input="updateInput"
  />
</template>

<script>
export default {
  name: 'InputTextArea',
  props: {
    modelValue: [String, Number]
  },
  methods: {
    updateInput(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style scoped lang="sass">
  textarea
    width: 100%
    height: 108px
    box-sizing: border-box
    padding: 10px 16px
    background: #FFFEFB
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1)
    border-radius: 4px
    border: none
    resize: none
    font-weight: 400
    font-size: 12px
    line-height: 15px
    &::placeholder
      font-weight: 400
      font-size: 12px
      line-height: 15px
      color: #B4B4B4
</style>