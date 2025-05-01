<script setup>
const props = defineProps({
    homeTeamName: {
        type: String,
        required: true,
    },
    homeTeamLogo: {
        default: null, // Is put as we can't be certain that the data is in the API
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
</script>

<template>
    <section id="game-score-box">
        <div id="teams">
            <div class="teamname-logo">
                <img :src="homeTeamLogo" alt="Hjemmehold logo">
                <p> {{ homeTeamName }} </p>
            </div>
            <p class="bold"> VS </p>
            <div class="teamname-logo">
                <img :src="awayTeamLogo" alt="Udehold logo">
                <p> {{ awayTeamName }} </p>
            </div>
        </div>
        <div id="score">
            <h2 class="bold"> {{ homeTeamScore }} </h2>
            <h2 class="bold"> - </h2>
            <h2 class="bold"> {{ awayTeamScore }} </h2>
        </div>
    </section>
</template>

<style scoped>
.bold {
    font-weight: 700;
}

#game-score-box {
    display: flex;
    flex-direction: column;
    padding: 15px;
    gap: 30px;
    border-radius: 10px;
    background-color: cadetblue;
}

#teams {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

#score {
    display: flex;
    justify-content: space-between;
    padding: 0px 30px;
}

.teamname-logo {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
}

.teamname-logo > img {
    max-width: 75px;
}
</style>