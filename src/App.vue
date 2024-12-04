<template>
  <div id="app">
    <TheHeader :name-card.sync="filerCardName" />
    <MainPage :cards="cards" :name-card="filerCardName"/>
    <TheFooter />
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import MainPage from './components/MainPage.vue';
import TheFooter from './components/TheFooter.vue';
import cards from '@/data/cards';
import './assets/style.css'
import './assets/media.css'

export default {
  data() {
    return {
      filerCardName: ''
    }
  },
  name: 'App',
  components: {
    TheHeader,
    MainPage,
    TheFooter
  },
  computed: {
    filteredCards() {
      let filteredCards = cards

      if (this.filerCardName) {
        filteredCards = filteredCards.filter(card => card.title.toLowerCase().includes(this.filerCardName.toLowerCase()))
      }
    
      return filteredCards
    },
    cards() {
      return this.filteredCards
    }
  }
}
</script>
