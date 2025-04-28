<script setup>
import FootballLatestStat from './FootballLatestStat.vue'
import { ref, onMounted } from 'vue';

const footballGames = ref([]);

async function GetGameData() {
    let response = await fetch("https://v3.football.api-sports.io/fixtures?league=120&season=2024&team=405&last=5", {
        method: "GET",
        headers: {
            "x-apisports-key": "10c1dce6b1c7f7e049a53bdbc7f8d164",
        },
    })
    let result = await response.json();

    console.log(result);

    footballGames.value = result.response;
}

onMounted(() => {
    GetGameData();
});
</script>

<template>
    <div id="stat-list">
        <h2> De 5 sidste kampe </h2>
        <FootballLatestStat v-for="game in footballGames" :key="game.fixture.id" :homeTeamName="game.teams.home.name"
            :homeTeamLogo="game.teams.home.logo" :homeTeamScore="game.goals.home" :awayTeamName="game.teams.away.name"
            :awayTeamLogo="game.teams.away.logo" :awayTeamScore="game.goals.away"/>
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