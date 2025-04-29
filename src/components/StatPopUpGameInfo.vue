<script setup>

</script>

<template>
    <section id="game-info-box">
        <div class="info-pair">
            <p class="bold"> Dommer: </p>
            <p> Dommernavn </p>
        </div>
        <div class="info-pair">
            <p class="bold"> Liga/turnering: </p>
            <p> Leaguenavn </p>
        </div>
        <div class="info-pair">
            <p class="bold"> By: </p>
            <p> Bynavn </p>
        </div>
        <div class="info-pair">
            <p class="bold"> Stadion: </p>
            <p> Stadion navn </p>
        </div>
        <div class="info-pair">
            <p class="bold"> Sæson: </p>
            <p> Årstal </p>
        </div>
        <div class="info-pair">
            <p class="bold"> Dato: </p>
            <p> Fuld dato </p>
        </div>
        <div class="info-pair">
            <p class="bold"> Antal tilskuere: </p>
            <p> Nummer </p>
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
}

.info-pair {
    display: flex;
    justify-content: space-between;
}
</style>