<script setup>
import { ref } from 'vue';

const homeTeamName = ref(null);
const homeTeamLogo = ref(null);
const awayTeamName = ref(null);
const awayTeamLogo = ref(null);
const gameDate = ref(null);

const countdownDays = ref(null);
const countdownHours = ref(null);
const countdownMinutes = ref(null);
const countdownSeconds = ref(null);

const fetchComplete = ref(false);

async function GetData() {
    let response = await fetch("https://v3.football.api-sports.io/fixtures?league=120&season=2024&team=405&next=1", {
        method: "GET",
        headers: {
            "x-apisports-key": "10c1dce6b1c7f7e049a53bdbc7f8d164",
        },
    })
    let result = await response.json();

    console.log(result);

    // Next Game Info
    const gameObject = result.response[0];

    homeTeamName.value = gameObject.teams.home.name; // Ændrer variablens value - finder name i objektet
    homeTeamLogo.value = gameObject.teams.home.logo; // Ændrer variablens value - finder logo i objektet

    awayTeamName.value = gameObject.teams.away.name; // Ændrer variablens value - finder name i objektet
    awayTeamLogo.value = gameObject.teams.away.logo; // Ændrer variablens value - finder logo i objektet

    gameDate.value = new Date(gameObject.fixture.date); // Ændrer variablens value - finder date i objektet

    SetupCountdown();
}
GetData();

function SetupCountdown() {
    setInterval(() => {
        const todaysDate = new Date().getTime(); // Hent og opbevar nuværende dato
        const distanceBetween = gameDate.value.getTime() - todaysDate; // Find distancen mellem nu og countdown datoen

        // Time calculations for days, hours, minutes and seconds
        const days = Math.floor(distanceBetween / (1000 * 60 * 60 * 24));
        const hours = Math.floor((distanceBetween % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((distanceBetween % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((distanceBetween % (1000 * 60)) / 1000);

        // Save info in variables
        countdownDays.value = days;
        countdownHours.value = hours;
        countdownMinutes.value = minutes;
        countdownSeconds.value = seconds;
    }, 1000)
}
</script>

<template>
    <div id="countdown-content">
        <h1> Næste Herre Kamp </h1>
        <div id="countdown-teams">
            <div class="team-logo-name">
                <img class="team-img" :src="homeTeamLogo" alt="Team logo">
                <h2> {{ homeTeamName }} </h2>
            </div>
            <div id="versus-text">
                <h2> vs. </h2>
            </div>
            <div class="team-logo-name">
                <img class="team-img" :src="awayTeamLogo" alt="Team logo">
                <h2> {{ awayTeamName }} </h2>
            </div>
        </div>
        <!-- <h2> {{ homeTeamName }} vs. {{ awayTeamName }} </h2> -->
        <p> {{ new Intl.DateTimeFormat("da-DK", {
            dateStyle: "full",
            timeStyle: "short",
        }).format(gameDate) }} </p>
        <div id="countdown">
            <div class="time-measurement">
                <h2> {{ countdownDays }} </h2>
                <p> Dage </p>
            </div>
            <div class="time-measurement">
                <h2> {{ countdownHours }} </h2>
                <p> Timer </p>
            </div>
            <div class="time-measurement">
                <h2> {{ countdownMinutes }} </h2>
                <p> Minutter </p>
            </div>
            <div class="time-measurement">
                <h2> {{ countdownSeconds }} </h2>
                <p> Sekunder </p>
            </div>
        </div>
    </div>
</template>

<style scoped>
h1 {
    font-weight: 700;
}

#countdown-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
    padding: 15px;
    min-width: 500px;
    background-color: darkslategray;
    border-radius: 10px;
}

#countdown-teams {
    display: flex;
    justify-content: center;
    gap: 25px;
    align-items: end;
}

.team-logo-name {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 15px;
}

.team-img {
    width: 100%;
    max-width: 65px;
}

/* #versus-text {
    display: flex;
} */

#countdown {
    display: flex;
    gap: 25px;
}

.time-measurement {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 50px;
    gap: 5px;
}
</style>