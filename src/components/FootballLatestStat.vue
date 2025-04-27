<script setup>

</script>

<template>
    <div id="game-stat">
        <div class="team-info">
            <img src="" alt="">
            <p> Hjemmehold </p>
        </div>
        <div>
            <p> X </p>
        </div>
        <div>
            <p> - </p>
        </div>
        <div>
            <p> X </p>
        </div>
        <div class="team-info">
            <img src="" alt="">
            <p> Udehold </p>
        </div>
    </div>
</template>

<style scoped>
#game-stat {
    display: flex;
    justify-content: space-between;
    background-color: darkslategray;
    padding: 10px;
}

.team-info {
    display: flex;
    flex-direction: column;
    gap: 5px;
    align-items: center;
}

.team-info > img {
    background-color: aquamarine;
    max-width: 50px;
}
</style>