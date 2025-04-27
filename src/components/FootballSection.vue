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
    gap: 40px;
    padding: 20px;
    margin: 40px;
    background-color: rgb(66, 107, 107);
}
</style>