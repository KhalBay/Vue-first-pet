<template>
  <input
      type="text"
      :value="value"
      @input="updateInput"
  >
</template>

<script>
export default {
  name: 'InputText',
  props: {
    value: [String, Number]
  },
  methods: {
    updateInput(event) {
      this.$emit('update:value', event.target.value)
    }
  }
}
</script>

<style scoped lang="sass">
  input
    width: 100%
    box-sizing: border-box
    padding: 10px 16px
    background: #FFFEFB
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1)
    border-radius: 4px
    border: 1px solid transparent
    font-weight: 400
    font-size: 12px
    line-height: 15px
    &::placeholder
      font-weight: 400
      font-size: 12px
      line-height: 15px
      color: #B4B4B4
</style>