<template>
    <div class="timer__add" v-on:click="$emit('add-timer')">
        <img src="../assets/images/add.png">
    </div>
</template>

<script>
    export default {
        name: "AddTimer"
    }
</script>

<style scoped>
    .timer__add{
        display: flex;
        justify-content: center;
        align-items: center;
        width: 225px;
        height: 120px;
        background: #696969;
        margin-bottom: 45px;
    }
</style>