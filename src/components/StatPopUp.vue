<script setup>
import StatPopUpStatistics from './StatPopUpStatistics.vue'
import StatPopUpScore from './StatPopUpScore.vue'
import StatPopUpGameInfo from './StatPopUpGameInfo.vue'

const props = defineProps({
    selectedGame: {
        type: Object,
        required: true,
    }
});
</script>

<template>
    <section id="game-pop-up">
        <div id="pop-up-header">
            <h2 class="bold"> Kampinformation </h2>
            <div>
                <!-- When user clicks on the img the closePopUp event will emit. The parent component 
                 FootballLatestStats listens after this event with help from @closePopUp="ClosePopUp" 
                 and then it executes its own ClosePopUp function to hide the pop-up -->
                <img @click="$emit('closePopUp')" src="../assets/illustrations/close.svg" alt="Kryds symbol">
            </div>
        </div>
        <div id="pop-up-components">
            <div id="components-score-gameinfo">
                <StatPopUpScore :homeTeamName="selectedGame.teams.home.name"
                    :homeTeamLogo="selectedGame.teams.home.logo" :homeTeamScore="selectedGame.goals.home"
                    :awayTeamName="selectedGame.teams.away.name" :awayTeamLogo="selectedGame.teams.away.logo"
                    :awayTeamScore="selectedGame.goals.away" />
                <StatPopUpGameInfo :referee="selectedGame.fixture.referee" :league="selectedGame.league.name"
                    :city="selectedGame.fixture.venue.city" :venue="selectedGame.fixture.venue.name"
                    :season="selectedGame.league.season" :date="new Date(selectedGame.fixture.date)" />
            </div>
            <StatPopUpStatistics />
        </div>
    </section>
</template>

<style scoped>
.bold {
    font-weight: 700;
}

#game-pop-up {
    display: flex;
    flex-direction: column;
    gap: 20px;
    width: 90%;
    max-width: 900px;
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