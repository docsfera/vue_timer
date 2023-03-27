<template>
    <div class="timer" :class="{active: timer.isPlay}">
        <p class="timer__title">{{getTime(timer.time)}}</p>
        <div class="timer__settings">
            <button class="play" v-on:click="$emit('play', timer.id)"></button>
            <button class="delete" v-on:click="$emit('delete-timer', timer.id)"></button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "TimerComponent",
        props: ['timer'],
        methods: {
            getTime(time){
                let hours = Math.floor(time / 60 / 60)
                let minutes = Math.floor(time / 60) - (hours * 60)
                let seconds = time % 60

                const formatter = (num) => {
                    return num < 10 ? `0${num}` : num
                }

                if(!hours && !minutes){
                    return seconds
                }
                if(!hours && minutes){
                    return `${minutes}:${formatter(seconds)}`
                }
                if(hours){
                    return `${hours}:${formatter(minutes)}:${formatter(seconds)}`
                }
            }
        }
    }
</script>

<style scoped>
    .timer{
        width: 225px;
        height: 120px;
        background: #696969;
        margin-bottom: 45px;
    }
    .active .timer__title{
        color: white;
    }
    .active .timer__settings{
        border-top: 1px solid white;
    }
    .active .timer__settings .play{
        background: url(../assets/images/pause.png) no-repeat center;
    }
    .active .timer__settings .delete{
        background: url(../assets/images/delete-active.png) no-repeat center;
    }
    .timer__title{
        font-family: "GothamPro", sans-serif;
        margin: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 60px;
        font-size: 22px;
        line-height: 21px;
        color: #9E9E9E;
    }
    .timer__settings{
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 60px;
        border-top: 1px solid #9E9E9E;
    }
    .timer button{
        width: 20px;
        height: 20px;
        border: none;
    }
    .play{
        background: url(../assets/images/play.png) no-repeat center;
        margin-right: 42px;
    }
    .delete{
        background: url(../assets/images/delete.png) no-repeat center;
    }
    @media (min-width: 1200px){
        .timer{
            margin-right: 50px;
        }
        .timer:nth-child(3n+3){
            margin-right: 0;
        }
    }

    @media (min-width: 769px) and (max-width: 1199px) {
        .timer{
            margin-right: 50px;
        }
        .timer:nth-child(2n){
            margin-right: 0;
        }
    }
</style>