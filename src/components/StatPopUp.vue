<script setup>
import StatPopUpStatistics from './StatPopUpStatistics.vue'
import StatPopUpScore from './StatPopUpScore.vue'
import StatPopUpGameInfo from './StatPopUpGameInfo.vue'
</script>

<template>
    <section id="game-pop-up">
        <div id="pop-up-header">
            <h2> Kampinformation </h2>
            <div>
                <img src="../assets/illustrations/close.svg" alt="Kryds symbol">
            </div>
        </div>
        <div id="pop-up-components">
            <div id="components-score-gameinfo">
                <StatPopUpScore />
                <StatPopUpGameInfo />
            </div>
            <StatPopUpStatistics />
        </div>
    </section>
</template>

<style scoped>
#game-pop-up {
    display: flex;
    flex-direction: column;
    gap: 20px;
    width: 100%;
    padding: 20px;
    border-radius: 10px;
    background-color: rgb(9, 34, 34);
}

#pop-up-header {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    width: 100%;
}

#pop-up-components {
    display: flex;
    gap: 20px;
}

#components-score-gameinfo {
    display: flex;
    flex-direction: column;
    gap: 20px;
    width: 100%;
    max-width: 250px;
}
</style>