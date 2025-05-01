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
    <div id="game-stat">
        <div class="team-info">
            <img :src="homeTeamLogo" alt="Hjemmehold logo">
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
            <img :src="awayTeamLogo" alt="Udehold logo">
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
    align-items: center;
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
    width: 20%;
}

.team-info>img {
    max-width: 50px;
}
</style>