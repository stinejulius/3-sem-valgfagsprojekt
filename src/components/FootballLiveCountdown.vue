<script setup>

</script>

<template>
    <div id="countdown-content">
        <h1> Næste Herre Kamp </h1>
        <h2> Hjemmehold vs. Udehold </h2>
        <p> Nummer Måned År </p>
        <div id="countdown">
            <div class="time-measurement">
                <h2> XX </h2>
                <p> Dage </p>
            </div>
            <div class="time-measurement">
                <h2> XX </h2>
                <p> Timer </p>
            </div>
            <div class="time-measurement">
                <h2> XX </h2>
                <p> Minutter </p>
            </div>
            <div class="time-measurement">
                <h2> XX </h2>
                <p> Sekunder </p>
            </div>
        </div>
    </div>
</template>

<style scoped>
#countdown-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
    padding: 15px;
    min-width: 500px;
    background-color: darkslategray;
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