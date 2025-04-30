<script setup>
import FootballLiveCountdown from './FootballLiveCountdown.vue'
import FootballLatestStats from './FootballLatestStats.vue'
</script>

<template>
    <section>
        <FootballLiveCountdown />
        <FootballLatestStats />
    </section>
</template>

<style scoped>
section {
    display: flex;
    flex-direction: column;
    gap: 20px;
    padding: 20px;
    margin: 20px auto;
    background-color: rgb(66, 107, 107);
    width: 100%;
    max-width: 700px;
    min-width: 500px;
}
</style>