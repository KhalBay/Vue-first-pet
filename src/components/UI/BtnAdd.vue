<template>
  <button>
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'BtnAdd',
}
</script>

<style lang="sass" scoped>
  button
    width: 100%
    box-sizing: border-box
    font-family: 'Inter'
    font-weight: 600
    font-size: 12px
    line-height: 15px
    color: #FFF
    background: #7BAE73
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1)
    border-radius: 10px
    border: none
    padding: 10px
    cursor: pointer
    &:focus-visible
      outline: none
    &:hover
      opacity: .7
</style>