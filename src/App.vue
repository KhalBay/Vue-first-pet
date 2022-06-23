<template>
  <div class="b-cont">
    <div class="layout">
      <header>
        <h2>Добавление товара</h2>
        <div class="select-wrap">
          <select-custom
              v-model="selectedSort"
              :options="sortOptions"
          />
        </div>
      </header>
      <form-add-stuff
          @create="createstuff"
      />
      <stuff-list
          :stuffs="stuffs"
          @remove="removeItem"
      />
    </div>
  </div>
</template>

<script>
  import StuffList from "@/components/StuffList";
  import FormAddStuff from "@/components/FormAddStuff";

  export default {
    components: {
      StuffList, FormAddStuff,
    },
    data() {
      return {
        stuffs: [
          {
            id: 1,
            title: 'Наименование товара',
            desc: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
            price: '10000',
            img: require('@/img/img.png'),
          },
          {
            id: 2,
            title: 'Наименование товара',
            desc: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
            price: '10000',
            img: require('@/img/img.png'),
          },
          {
            id: 3,
            title: 'Наименование товара',
            desc: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
            price: '10000',
            img: require('@/img/img.png'),
          },
          {
            id: 4,
            title: 'Наименование товара',
            desc: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
            price: '10000',
            img: require('@/img/img.png'),
          },
          {
            id: 5,
            title: 'Наименование товара',
            desc: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
            price: '10000',
            img: require('@/img/img.png'),
          },
          {
            id: 6,
            title: 'Наименование товара',
            desc: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
            price: '10000',
            img: require('@/img/img.png'),
          },
        ],
        selectedSort: '',
        sortOptions: [
          {value: 'price', name: 'По цене min'},
          {value: 'price', name: 'По цене max'},
          {value: 'title', name: 'По наименованию'},
        ],
      }
    },
    methods: { //Добавление удаление товаров
      createstuff(stuff) {
        this.stuffs.push(stuff);
      },
      removeItem(stuff) {
        this.stuffs = this.stuffs.filter(s => s.id !== stuff.id)
      }
    },
    watch: { //Сортировка, не знаю как сделать для цены, но по названию отрабатывает
      selectedSort(newValue) {
        this.stuffs.sort((stuff1, stuff2) => {
          return stuff1[newValue]?.localeCompare(stuff2[newValue])
        })
      }
    }
  }
</script>

<style lang="sass">
  @import fonts/fonts.css
  @import sass/mixin.sass

  *
    margin: 0
    padding: 0
    box-sizing: border-box
    font-family: 'Source Sans Pro'
    font-weight: 600
    color: #3F3F3F

  .b-cont
    display: flex
    justify-content: center
    width: 100%
    height: 100%
    padding: 32px
    .layout
      display: grid
      grid-template-columns: repeat(16, 71px)
      gap: 16px
      +media(1400px)
        grid-template-columns: repeat(16, 1fr)
      +media(998px)
        display: flex
        flex-direction: column

      header
        grid-column: 1/17
        display: flex
        justify-content: space-between
        align-items: center
        h2
          font-size: 28px
          line-height: 35px

        .select-wrap
          position: relative
          +media(998px)
            position: absolute
            top: 540px

          &::before
            content: ''
            position: absolute
            top: 14px
            right: 15px
            width: 5px
            height: 5px
            border-bottom: 1px solid #B4B4B4
            border-right: 1px solid #B4B4B4
            transform: rotate(45deg)

</style>