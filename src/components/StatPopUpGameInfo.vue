<script setup>
const props = defineProps({
    referee: {
        type: String,
        required: null, // Sættes da man ikke kan være sikker på at det findes i API
    },
    league: {
        type: String,
        default: null,
    },
    city: {
        type: String,
        default: null,
    },
    venue: {
        type: String,
        required: null,
    },
    season: {
        type: String,
        default: null,
    },
    date: {
        type: Date,
        default: null,
    },
});
</script>

<template>
    <section id="game-info-box">
        <div class="info-pair">
            <p class="bold"> Dommer: </p>
            <p> {{ referee }} </p>
        </div>
        <div class="info-pair">
            <p class="bold"> Liga/turnering: </p>
            <p> {{ league }} </p>
        </div>
        <div class="info-pair">
            <p class="bold"> By: </p>
            <p> {{ city }} </p>
        </div>
        <div class="info-pair">
            <p class="bold"> Stadion: </p>
            <p> {{ venue }} </p>
        </div>
        <div class="info-pair">
            <p class="bold"> Sæson: </p>
            <p> {{ season }} </p>
        </div>
        <div class="info-pair">
            <p class="bold"> Dato: </p>
            <p> {{ new Intl.DateTimeFormat("da-DK", {
                dateStyle: "short",
                timeStyle: "short",
            }).format(date) }} </p>
        </div>
    </section>
</template>

<style scoped>
.bold {
    font-weight: 700;
}

#game-info-box {
    display: flex;
    flex-direction: column;
    gap: 10px;
    padding: 15px;
    background-color: cadetblue;
    border-radius: 10px;
    height: 100%;
}

.info-pair {
    display: flex;
    justify-content: space-between;
}
</style>