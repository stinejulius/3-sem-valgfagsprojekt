<script setup>
import FootballLatestStat from './FootballLatestStat.vue'
import StatPopUp from './StatPopUp.vue'
import { ref, onMounted } from 'vue';

const footballGames = ref([]);

async function GetGameData() {
    const response = await fetch("https://v3.football.api-sports.io/fixtures?league=120&season=2024&team=405&last=5", {
        method: "GET",
        headers: {
            "x-apisports-key": "10c1dce6b1c7f7e049a53bdbc7f8d164",
        },
    })
    const result = await response.json();

    console.log(result);

    footballGames.value = result.response;
}

onMounted(() => {
    GetGameData();
});

const selectedFootballGameId = ref(null);

function OpenPopUp(footballGameId) {
    selectedFootballGameId.value = footballGameId;
}

function ClosePopUp() {
    selectedFootballGameId.value = null;
}

function GetGameByGameId(footballGameId) {
    return footballGames.value.find((footballGame) => {
        if (footballGame.fixture.id === footballGameId) {
            return true;
        }

        return false;
    });
}

</script>

<template>
    <div id="stat-list">
        <h2> De 5 sidste kampe </h2>
        <FootballLatestStat v-for="footballGame in footballGames" :key="footballGame.fixture.id"
            @click="OpenPopUp(footballGame.fixture.id)" :homeTeamName="footballGame.teams.home.name"
            :homeTeamLogo="footballGame.teams.home.logo" :homeTeamScore="footballGame.goals.home"
            :awayTeamName="footballGame.teams.away.name" :awayTeamLogo="footballGame.teams.away.logo"
            :awayTeamScore="footballGame.goals.away" />
    </div>

    <div id="pop-up" v-if="selectedFootballGameId !== null">
        <StatPopUp :selectedGame="GetGameByGameId(selectedFootballGameId)"
            @closePopUp="ClosePopUp" />
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

#pop-up {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 100;

    /* Glassmorphism */
    backdrop-filter: blur(10px);
    background: rgba(255, 255, 255, 0.116);
}
</style>