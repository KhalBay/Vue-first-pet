<template>
  <button>
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'BtnDel',
}
</script>

<style scoped lang="sass">
button
  position: absolute
  top: -8px
  right: -8px
  width: 32px
  height: 32px
  background: #FF8484
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1)
  border-radius: 10px
  border: none
  cursor: pointer
  display: none
  &::before
    content: ''
    position: absolute
    top: 8px
    left: 8px
    width: 16px
    height: 16px
    background: url('@/img/trash.svg') no-repeat center
  &:hover
    opacity: .7

</style>