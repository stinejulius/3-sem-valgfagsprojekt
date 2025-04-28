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
    margin: 20px;
    background-color: rgb(66, 107, 107);
    width: 100%;
    max-width: 600px;
    min-width: 400px;
}
</style>