<template>
  <div v-if="stuffs.length" class="stuff-list">
    <transition-group name="stuff-list">
      <stuff-item
          v-for="stuff in stuffs"
          :stuff="stuff"
          :key="stuff.id"
          @remove="$emit('remove', stuff)"
      />
    </transition-group>
  </div>
  <div v-else class="Easter-Egg">
    <h1>Упс.. Все удалено</h1>
    <img src="@/img/null.jpg">
  </div>
</template>

<script>
import StuffItem from "@/components/StuffItem";

export default {
  components: {
    StuffItem,
  },
  props: {
    stuffs: {
      type: Array,
      required: true,
    }
  }
}
</script>

<style scoped lang="sass">
  @import "~@/sass/mixin.sass"

  .stuff-list
    grid-column: 5/17
    display: grid
    grid-template-columns: repeat(3, minmax(0px, 1fr))
    gap: 16px
    +media(760px)
      grid-template-columns: repeat(2, minmax(0px, 1fr))
    +media(520px)
      grid-template-columns: repeat(1, minmax(0px, 1fr))

  .Easter-Egg
    grid-column: 5/17
    display: flex
    flex-direction: column
    img
      width: 400px
      height: 400px

  //анимация
  .stuff-list-move, .stuff-list-enter-active, .stuff-list-leave-active
    transition: all 0.5s ease

  .stuff-list-enter-from, .stuff-list-leave-to
    opacity: 0
    transform: translateX(30px)

  .stuff-list-leave-active
    position: absolute
</style>