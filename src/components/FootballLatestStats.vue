<script setup>
import FootballLatestStat from './FootballLatestStat.vue'
import StatPopUp from './StatPopUp.vue'
import { ref, onMounted } from 'vue';

const footballGames = ref([]);
const selectedFootballGameId = ref(null); // Meant to save the ID of the game that has been chosen to get shown in the pop-up

/**
 * Async. fetches data about the latest 5 games from API.
 * Updates variable footballGames value.
 */
async function GetGameData() {
    const response = await fetch("https://proxy.binau.dev/api/proxy/football/fixtures?league=120&season=2024&team=405&last=5", {
        method: "GET",
        headers: {
            "x-apisports-key": "10c1dce6b1c7f7e049a53bdbc7f8d164",
        },
    })
    const result = await response.json();

    footballGames.value = result.response;
}

onMounted(() => {
    /**
    * onMounted ensures that the GetGameData function only gets called when the
    * FootballLatestStats component has been mounted in the DOM. 
    */
    GetGameData(); // Calls GetGameData()
});

/**
 * Changes selectedFootballGameId to the ID of a specific selected football game 
 * (triggers pop-up to open).
 * @param {number} footballGameId - Specific game ID
 */
function OpenPopUp(footballGameId) {
    selectedFootballGameId.value = footballGameId;
}

/**
 * Changes selectedFootBallGameId to null (triggers pop-up to close).
 */
function ClosePopUp() {
    selectedFootballGameId.value = null;
}

/**
 * Finds and returns a specific football game object from the 'footballGames'
 * array based on its unique ID.
 * @param {number} footballGameId - Specific game ID
 * @returns {object} - football game object
 */
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
        <!-- The v-for is used to go through the footballGames array.
        For  every footballGame in the array a FootballLatestStat component will be rendered. -->
        <FootballLatestStat v-for="footballGame in footballGames" :key="footballGame.fixture.id"
            @click="OpenPopUp(footballGame.fixture.id)" :homeTeamName="footballGame.teams.home.name"
            :homeTeamLogo="footballGame.teams.home.logo" :homeTeamScore="footballGame.goals.home"
            :awayTeamName="footballGame.teams.away.name" :awayTeamLogo="footballGame.teams.away.logo"
            :awayTeamScore="footballGame.goals.away" />
    </div>
    <!-- v-if secures that this div only gets rendered when selectedFootballGameId isn't null. -->
    <div id="pop-up" v-if="selectedFootballGameId !== null">
        <StatPopUp :selectedGame="GetGameByGameId(selectedFootballGameId)" @closePopUp="ClosePopUp" />
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