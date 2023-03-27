<template>
 <div class="main">
  <TimerComponent
          v-for="timer of timers"
          v-bind:timer="timer"
          v-bind:key="timer.id"
          @delete-timer="deleteTimer"
          @play="play"

  />
  <AddTimer @add-timer="addTimer"/>
 </div>

</template>

<script>
 import TimerComponent from "@/components/TimerComponent"
 import AddTimer from "@/components/AddTimer"

    export default {
        name: "MainComponent",
        props: ['timers'],
        components: {
         TimerComponent, AddTimer
        },
        methods: {
         deleteTimer(id){
          this.$emit('delete-timer', id)
         },
         addTimer(){
          this.$emit('add-timer', {id: Date.now(), time: 0, isPlay: false, interval: ""})
         },
         play(id){
          this.$emit('play', id)
         }
        }
    }
</script>

<style scoped>
    .main{
        display: flex;
        flex-wrap: wrap;
        width: 100%;
        height: 100%;
    }
    @media (min-width: 1200px){
        .main{
            width: 775px;
        }
    }

    @media (min-width: 769px) and (max-width: 1199px) {
        .main{
            width: 500px;
            flex-direction: row;
            flex-wrap: wrap;
        }
    }
    @media (min-width: 320px) and (max-width: 768px) {
        .main{
            width: 225px;
            flex-direction: column;
            flex-wrap: nowrap;
        }
    }
    @media (max-width: 319px){
        .main{
            justify-content: center;
        }
    }
</style>