<script setup>

</script>

<template>
    <section id="statistics-box">
        <div id="goal-score">
            <h3 class="bold"> Målscore </h3>
            <div class="goal-score-team">
                <p class="bold"> Hjemmehold: </p>
                <p> [spiller fulde navn] (minut i kamp), [spiller fulde navn] (minut i kamp) </p>
            </div>
            <div class="goal-score-team">
                <p class="bold"> Udehold: </p>
                <p> [spiller fulde navn] (minut i kamp), [spiller fulde navn] (minut i kamp) </p>
            </div>
        </div>
        <div id="statistics">
            <h3 class="bold"> Statistik </h3>
            <table id="table">
                <thead id="table-head">
                    <tr>
                        <th>  </th>
                        <th> Hjemmehold </th>
                        <th> Udehold </th>
                    </tr>
                </thead>
                <tbody id="table-body">
                    <tr>
                        <th> Skud (På mål / Forbi) </th>
                        <th> X / Y </th>
                        <th> X / Y </th>
                    </tr>
                    <tr>
                        <th> Hjørneskud </th>
                        <th> X </th>
                        <th> X </th>
                    </tr>
                    <tr>
                        <th> Frispark (Begået / Tilkendt) </th>
                        <th> X / Y </th>
                        <th> X / Y </th>
                    </tr>
                    <tr>
                        <th> Offsides </th>
                        <th> X </th>
                        <th> X </th>
                    </tr>
                    <tr>
                        <th> Redninger (Målmænd) </th>
                        <th> X </th>
                        <th> X </th>
                    </tr>
                    <tr>
                        <th> Tacklinger (Vundet / Tabt) </th>
                        <th> X / Y </th>
                        <th> X / Y </th>
                    </tr>
                    <tr>
                        <th> Afleveringer (Præcision) </th>
                        <th> X % </th>
                        <th> X % </th>
                    </tr>
                    <tr>
                        <th> Gule kort </th>
                        <th> X </th>
                        <th> X </th>
                    </tr>
                    <tr>
                        <th> Røde kort </th>
                        <th> X </th>
                        <th> X </th>
                    </tr>
                </tbody>
            </table>
        </div>
    </section>
</template>

<style scoped>
.bold {
    font-weight: 700;
}

#statistics-box {
    display: flex;
    flex-direction: column;
    padding: 15px;
    gap: 30px;
    border-radius: 10px;
    background-color: cadetblue;
    width: 100%;
}

#goal-score {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.goal-score-team {
    display: flex;
    justify-content: space-between;
}
</style>