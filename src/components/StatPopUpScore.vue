<script setup>

</script>

<template>
    <section id="game-score-box">
        <div id="teams">
            <div class="teamname-logo">
                <img src="" alt="">
                <p> Hjemmehold </p>
            </div>
            <p> VS </p>
            <div class="teamname-logo">
                <img src="" alt="">
                <p> Udehold </p>
            </div>
        </div>
        <div id="score">
            <h2> X </h2>
            <h2> - </h2>
            <h2> X </h2>
        </div>
    </section>
</template>

<style scoped>
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