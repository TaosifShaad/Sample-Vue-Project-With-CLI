<template>
  <div id="app">
  <h1>Your upcoming destinations</h1>
  <div class="location-contain">
    <div class="locations">
      <TravelCard v-for="location in locationsAll" :key="location.name" :card="location"></TravelCard>
    </div>
    <h1>Welcome to Hotel California</h1>
    <button @click="toggle">
        <span v-if="isShowing">Hide</span>
        <span v-else>Show</span> 
    </button>
    <transition name="fade">
      <modal v-if="isShowing">
          <button @click="toggle">But You Can Never Leave!</button>
      </modal>
    </transition>
  </div>
</div>
</template>

<script>
  import {reactive, toRefs} from 'vue';
  import TravelCard from '@/components/TravelCard.vue';
  import modal from '@/components/modal.vue';

  export default {
    components: {
      TravelCard,
      modal
    },
    setup(props) {
      const state = reactive({
        locationsAll: [
        {
          name: 'moscow',
          img: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/28963/moscow.svg',
          desc: `Moscow is the capital and most populous city of Russia, with 13.2 million residents within the city limits and 17.8 million within the urban area. Moscow has the status of a Russian federal city.`
        },
        {
          name: 'paris',
          img: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/28963/paris1.svg',
          desc: `Paris is the capital and most populous city of France. By the 17th century, Paris was one of Europe's major centres of finance, commerce, fashion, science, and the arts, and it retains that position still today.`
        },
        {
          name: 'rome',
          img: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/28963/rome.svg',
          desc: `Rome's history spans more than 2,500 years. While Roman mythology dates the founding of Rome at around 753 BC, the site has been inhabited for much longer, making it one of the oldest continuously occupied sites in Europe.`
        },
        {
          name: 'paris',
          img: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/28963/paris2.svg',
          desc: `By the end of the 12th century, Paris had become the political, economic, religious, and cultural capital of France. Maurice de Sully undertook the construction of the Notre Dame Cathedral at its eastern extremity.`
        },
      ],
      isShowing: false
      });

      function toggle() {
          state.isShowing = !state.isShowing;
          console.log("clicking");
      }
      return {
        ...toRefs(state),
        toggle,
      }
    }
  }
</script>

<style scoped>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  body {
    width: 100vw;
    height: 100vh;
    font-family: 'NTR', sans-serif;
    background: #eee;
  }
  h1 {
    text-align: center;
  }
  .locations {
    display: flex;
    justify-content: center;
  }
  .place {
    display: flex;
    flex-direction: column;
    width: 280px;
    height: 420px;
    justify-content: center;
    background: white;
    border: 3px solid #ddd;
    padding: 20px 20px;
    margin: 10px;
  }
  h2 {
    margin: 0;
    text-align: center;
  }
  img {
    margin: 10px;
  }
  button {
    background: none;
    border: solid 1px;
    border-radius: 2em;
    font: inherit;
    padding: 0.75em 2em;
    color: #4fc08d;
  }
  .fade-enter-from, .fade-leave-to {
    opacity: 0;
  }
  .fade-enter-active {
    transition: opacity 0.25s ease-out;
  }
  .fade-leave-active {
    transition: opacity 0.20s ease-in;
  }
</style>
