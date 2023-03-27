<template>
  <MainComponent
          v-bind:timers="timers"
          @delete-timer="deleteTimer"
          @add-timer="addTimer"
          @play="play"
  />
</template>

<script>
import MainComponent from './components/MainComponent.vue'


export default {
  name: 'App',
  components: {
    MainComponent
  },
  data(){
    return {
      timers: []
    }
  },
  methods: {
    deleteTimer(id){
      this.play(id, true)
      this.timers = this.timers.filter(t => t.id !== id)
    },
    addTimer(timer){
      this.timers.push(timer)
    },
    play(id, isDelete) {
      let timer = this.timers.find(t => t.id === id)
      clearInterval(timer.interval)
      timer.isPlay = !timer.isPlay
      if(!isDelete && timer.isPlay){
        timer.interval = setInterval(() => {
          timer.time++
        }, 1000)
      }
    }
  }
}
</script>

<style>
    @font-face {
        font-family: "GothamPro";
        src: url("assets/fonts/GothamPro.woff2");
    }
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        display: flex;
        justify-content: center;
        padding: 72px 133px 72px 135px;
    }
    @media (min-width: 320px) and (max-width: 768px) {
        #app{
            padding: 72px 49px 72px 46px;
        }
    }
    @media (max-width: 319px){
        #app{
            padding: 72px 0 72px 0;
        }
    }
</style>
