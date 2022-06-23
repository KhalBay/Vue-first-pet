<template>
  <div class="stuff-item">
    <img :src='stuff.img'>
    <div class="stuff-item__content">
      <div class="content-title">{{ stuff.title }}</div>
      <div class="content-desc">{{ stuff.desc }}</div>
      <div class="content-price">{{ stuff.price.toLocaleString('ru') }}</div>
    </div>
    <BtnDel class="stuff-item__btn" @click="$emit('remove', stuff)"></BtnDel>
  </div>
</template>

<script>
  export default {
    props: {
      stuff: {
        type: Object,
        required: true,
      }
    }
  }
</script>

<style scoped lang="sass">
.stuff-item
  background: #FFFEFB
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02)
  border-radius: 4px
  position: relative
  display: flex
  flex-direction: column
  img
    width: 100%
    border-radius: 4px 4px 0 0
    height: auto
    object-fit: cover

  &__content
    padding: 16px
    display: flex
    flex-direction: column
    justify-content: space-between
    height: 100%
    .content-title
      font-size: 20px
      line-height: 25px
      margin: 0 0 16px 0

    .content-desc
      font-weight: 400
      font-size: 16px
      line-height: 20px
      margin: 0 0 32px 0

    .content-price
      position: relative
      font-size: 24px
      line-height: 30px
      margin: 0 0 8px 0
      place-self: flex-start
      padding: 0 52px 0 0
      &::after
        content: 'руб.'
        position: absolute
        top: 0
        right: 0
        display: block

  &:hover .stuff-item__btn
    display: block

</style>