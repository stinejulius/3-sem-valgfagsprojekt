<script setup>
import { ref } from 'vue';

const homeTeamName = ref(null);
const homeTeamLogo = ref(null);
const homeTeamScore = ref(null);
const awayTeamName = ref(null);
const awayTeamLogo = ref(null);
const awayTeamScore = ref(null);

// const homeTeamName2 = ref(null);
// const homeTeamScore2 = ref(null);
// const awayTeamName2 = ref(null);
// const awayTeamScore2 = ref(null);

// const homeTeamName3 = ref(null);
// const homeTeamScore3 = ref(null);
// const awayTeamName3 = ref(null);
// const awayTeamScore3 = ref(null);

// const homeTeamName4 = ref(null);
// const homeTeamScore4 = ref(null);
// const awayTeamName4 = ref(null);
// const awayTeamScore4 = ref(null);

// const homeTeamName5 = ref(null);
// const homeTeamScore5 = ref(null);
// const awayTeamName5 = ref(null);
// const awayTeamScore5 = ref(null);




const props = defineProps({
    homeTeamName: {
        type: String,
        required: true,
    },
    homeTeamLogo: {
        default: null,
    },
    homeTeamScore: {
        type: Number,
        default: null,
    },
    awayTeamName: {
        type: String,
        required: true,
    },
    awayTeamLogo: {
        default: null,
    },
    awayTeamScore: {
        type: Number,
        default: null,
    },
});






async function GetData() {
    let response = await fetch("https://v3.football.api-sports.io/fixtures?league=120&season=2024&team=405&last=5", {
        method: "GET",
        headers: {
            "x-apisports-key": "10c1dce6b1c7f7e049a53bdbc7f8d164",
        },
    })
    let result = await response.json();

    console.log(result);

    const gameObject1 = result.response[0];
    const gameObject2 = result.response[1];
    const gameObject3 = result.response[2];
    const gameObject4 = result.response[3];
    const gameObject5 = result.response[4];

    // 1. Game info
    homeTeamName1.value = gameObject1.teams.home.name;
    homeTeamScore1.value = gameObject1.goals.home;
    awayTeamName1.value = gameObject1.teams.away.name;
    awayTeamScore1.value = gameObject1.goals.away;

    homeTeamName.value = [
        gameObject1.teams.home.name, 
        gameObject2.teams.home.name, 
        gameObject3.teams.home.name, 
        gameObject4.teams.home.name, 
        gameObject5.teams.home.name, 
    ]


    // En for loop, looper igennem et array med alle kamp informationerne (for de 5 sidste kampe), 
    // for hver gang den har gået igennem arrayet spytter den det ud i stat komponentets html







}

GetData();






</script>

<template>
    <div id="game-stat">
        <div class="team-info">
            <img :src="homeTeamLogo" alt="Team logo">
            <p class="bold"> {{ homeTeamName }} </p>
        </div>
        <div>
            <h2> {{ homeTeamScore }} </h2>
        </div>
        <div>
            <h2 class="bold"> - </h2>
        </div>
        <div>
            <h2> {{ awayTeamScore }} </h2>
        </div>
        <div class="team-info">
            <img :src="awayTeamLogo" alt="Team logo">
            <p class="bold"> {{ awayTeamName }} </p>
        </div>
    </div>
</template>

<style scoped>
.bold {
    font-weight: 700;
}

#game-stat {
    display: flex;
    justify-content: space-between;
    background-color: rgb(27, 54, 54);
    padding: 15px;
    width: 100%;
    border-radius: 10px;
}

.team-info {
    display: flex;
    flex-direction: column;
    gap: 5px;
    align-items: center;
}

.team-info>img {
    background-color: aquamarine;
    max-width: 50px;
}
</style>