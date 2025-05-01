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

/**
 * Async. fetches data for the next football game (w. specific team, league and season).
 * Updates ref variables (logo, name and date).
 * Calls SetupCountdown function.
 */
async function GetData() {
    const response = await fetch("https://v3.football.api-sports.io/fixtures?league=120&season=2024&team=405&next=1", {
        method: "GET",
        headers: {
            "x-apisports-key": "10c1dce6b1c7f7e049a53bdbc7f8d164",
        },
    })
    const result = await response.json();

    // Updates Game Info
    const gameObject = result.response[0];

    homeTeamName.value = gameObject.teams.home.name; // Changes the variables value - finds name in object
    homeTeamLogo.value = gameObject.teams.home.logo;

    awayTeamName.value = gameObject.teams.away.name;
    awayTeamLogo.value = gameObject.teams.away.logo;

    gameDate.value = new Date(gameObject.fixture.date);

    SetupCountdown(); // Calls SetupCountdown() when data has been fetched and placed
}
GetData();

/**
 * Sets an interval that runs every second.
 * Interval calculates and updates the countdown.
 */
function SetupCountdown() {
    setInterval(() => {
        const todaysDate = new Date().getTime(); // Get and keep the current date
        const distanceBetween = gameDate.value.getTime() - todaysDate; // FInd the distance between now and the game date

        // Time calculations for days, hours, minutes and seconds
        const days = Math.floor(distanceBetween / (1000 * 60 * 60 * 24));
        const hours = Math.floor((distanceBetween % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((distanceBetween % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((distanceBetween % (1000 * 60)) / 1000);

        // Update info in variables
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
                <img class="team-img" :src="homeTeamLogo" alt="Team logo"> <!-- : makes it possible to "grab" homeTeamLogo from script -->
                <h2> {{ homeTeamName }} </h2>
            </div>
            <div id="versus-text">
                <h2 class="bold"> vs. </h2>
            </div>
            <div class="team-logo-name">
                <img class="team-img" :src="awayTeamLogo" alt="Team logo">
                <h2> {{ awayTeamName }} </h2>
            </div>
        </div>
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
.bold {
    font-weight: 700;
}

h1 {
    font-weight: 700;
}

#countdown-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
    padding: 15px;
    width: 100%;
    background-color: darkslategray;
    border-radius: 10px;
}

#countdown-teams {
    display: flex;
    justify-content: space-evenly;
    gap: 25px;
    align-items: start;
    width: 80%;
}

.team-logo-name {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 15px;
    width: 40%;
}

.team-img {
    width: 100%;
    max-width: 65px;
}

#versus-text {
    padding-top: 15px;
}

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