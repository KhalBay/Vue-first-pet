<template>
  <form @submit.prevent>
    <label>
      <div class="label-title required">Наименование товара</div>
      <InputText
          v-model:value="stuff.title"
          @update:value="validateForm"
          type="text"
          placeholder="Введите наименование товара"
      />
      <div>Поле является обязательным</div>
    </label>
    <label>
      <div class="label-title">Описание товара</div>
      <InputTextArea
          v-model="stuff.desc"
          placeholder="Введите описание товара"
      />
    </label>
    <label>
      <div class="label-title required">Ссылка на изображение товара</div>
      <InputText
          v-model:value="stuff.img"
          @update:value="validateForm"
          type="text"
          placeholder="Введите ссылку"
      />
      <div>Поле является обязательным</div>
    </label>
    <label>
      <div class="label-title required">Цена товара</div>
      <InputText
          v-model:value="stuff.price"
          @update:value="validateForm"
          type="text"
          placeholder="Введите цену"
      />
      <div>Поле является обязательным</div>
    </label>
    <BtnAdd
        v-model="stuff.btn"
        class="btn-add"
        :class="{noneValid: is_valid}"
        @click="createStuff"
    >
      Добавить товар
    </BtnAdd>
  </form>
</template>

<script>
export default {
  data() {
    return {
      stuff: {
        title: '',
        desc: '',
        img: '',
        price: '',
      },
      is_valid: true,
      inputArr: '',
    }
  },
  methods: {
    validateForm() {//Валидация
      if (this.stuff.title && this.stuff.img && this.stuff.price) {
        this.is_valid = false
      } else {
        this.is_valid = true
      }
      this.inputArr = document.querySelectorAll('.required + input')
      this.inputArr.forEach(inpt => {
        if (inpt.value) {
          inpt.classList.remove('hasError')
        }
      })
    },
    createStuff() {//Добавление товара в список
      if (!this.is_valid) {
        this.stuff.id = Date.now();
        this.$emit('create', this.stuff)
        this.stuff = {
          title: '',
          desc: '',
          img: '',
          price: '',
        }
        this.is_valid = true

      } else {
        this.inputArr = document.querySelectorAll('.required + input');
        this.inputArr.forEach(inpt => {
          if (!inpt.value) {
            inpt.classList.add('hasError')
          }
        })
      }
    },

  }
}
</script>

<style scoped lang="sass">
  @import '~@/sass/mixin.sass'

  form
    grid-column: 1/5
    width: 100%
    height: 440px
    padding: 24px
    background: #FFFEFB
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02)
    border-radius: 4px
    position: sticky
    top: 20px
    +media(998px)
      position: relative
      top: 0
      margin: 0 0 50px 0

    label
      font-weight: 400
      font-size: 10px
      line-height: 13px
      color: #49485E
      display: flex
      flex-direction: column
      gap: 4px
      margin: 0 0 16px 0
      position: relative
      .required
        position: relative
        place-self: self-start
        &::before
          content: ''
          position: absolute
          top: 0
          right: -4px
          display: block
          width: 4px
          height: 4px
          border-radius: 4px
          background-color: #FF8484

      input + div
        display: none

      input.hasError
        border: 1px solid #FF8484

      input.hasError + div
        display: block
        position: absolute
        bottom: -12px
        font-weight: 400
        font-size: 8px
        line-height: 10px
        color: #FF8484

    .btn-add
      margin: 8px 0 0 0
      &.noneValid
        filter: grayscale(1)
        opacity: 1
        cursor: unset

</style>