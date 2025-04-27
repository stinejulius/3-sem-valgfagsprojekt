<script setup>
import FootballLatestStat from './FootballLatestStat.vue'
</script>

<template>
    <div id="stat-list">
        <FootballLatestStat />
        <FootballLatestStat />
        <FootballLatestStat />
        <FootballLatestStat />
        <FootballLatestStat />
    </div>
</template>

<style scoped>
#stat-list {
    display: flex;
    flex-direction: column;
    gap: 15px;
}
</style>