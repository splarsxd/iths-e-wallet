<template>
  <div class="wrapper">
    <header>
      <div class="title">
        <h1>E-WALLET</h1>
      </div>
    </header>

    <main>
      <article class="active">
        <h6>ACTIVE CARD</h6>
        <card v-bind:card="cards[this.position]" />
      </article>

      <article class="stacks">
        <card v-for="(card, index) in cards"
          :key="index"
          :card="cards[index]"
          @activated="activated(index)" />
      </article>

      <div class="addnew">
        <a href="/addcard">ADD A NEW CARD</a>
      </div>
    </main>
  </div>
</template>

<script>
import card from "../components/card.vue"
export default {
  data() {
    return {
      position: 0
    }
  },
  methods: {
    activated(index) {
      this.position = index
    }
  },
  components: {
    card
  },
  computed: {
    cards() {
      return this.$root.card
    }
  }
}
</script>

<style lang="sass" scoped>
a
  width: 10%
  color: #2d2d2d
  text-decoration: none
  font-weight: 600
  padding: 10px 20px

  display: flex
  justify-content: center
  margin: auto
  margin-top: 20px
  border-radius: 5px
  border: 1px solid #000
  color: #404040
  background-color: #b5b5b5

.stacks
  margin-top: 200px
  /deep/ .card
    margin-top: -150px
</style>