<script setup>
import FootballLatestStat from './FootballLatestStat.vue'
</script>

<template>
    <div id="stat-list">
        <h2> De 5 sidste kampe </h2>
        <FootballLatestStat />
        <FootballLatestStat />
        <FootballLatestStat />
        <FootballLatestStat />
        <FootballLatestStat />
    </div>
</template>

<style scoped>
h2 {
    font-weight: 700;
}

#stat-list {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 15px;
    background-color: darkslategray;
    padding: 15px;
    border-radius: 10px;
}
</style>