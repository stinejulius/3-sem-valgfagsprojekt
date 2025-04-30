<script setup>
// The API does not include the information needed for 1.Division :(
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
                        <th class="bold"> Hjemmehold </th>
                        <th class="bold"> Udehold </th>
                    </tr>
                </thead>
                <tbody id="table-body">
                    <tr>
                        <th class="bold"> Skud (På mål / Forbi) </th>
                        <th> X / Y </th>
                        <th> X / Y </th>
                    </tr>
                    <tr>
                        <th class="bold"> Hjørneskud </th>
                        <th> X </th>
                        <th> X </th>
                    </tr>
                    <tr>
                        <th class="bold"> Frispark (Begået / Tilkendt) </th>
                        <th> X / Y </th>
                        <th> X / Y </th>
                    </tr>
                    <tr>
                        <th class="bold"> Offsides </th>
                        <th> X </th>
                        <th> X </th>
                    </tr>
                    <tr>
                        <th class="bold"> Redninger (Målmænd) </th>
                        <th> X </th>
                        <th> X </th>
                    </tr>
                    <tr>
                        <th class="bold"> Tacklinger (Vundet / Tabt) </th>
                        <th> X / Y </th>
                        <th> X / Y </th>
                    </tr>
                    <tr>
                        <th class="bold"> Afleveringer (Præcision) </th>
                        <th> X % </th>
                        <th> X % </th>
                    </tr>
                    <tr>
                        <th class="bold"> Gule kort </th>
                        <th> X </th>
                        <th> X </th>
                    </tr>
                    <tr>
                        <th class="bold"> Røde kort </th>
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

.goal-score-team :first-child {
    padding-right: 10px;
}

#statistics {
    display: flex;
    flex-direction: column;
    gap: 10px;
    width: 100%;
}

#table {
    table-layout: fixed;
    width: 100%;
    border: 3px solid rgb(27, 54, 54);
    border-radius: 10px;
    border-collapse: collapse;
    border-style: hidden; /* hide standard table (collapsed) border */
    box-shadow: 0 0 0 3px rgb(27, 54, 54); /* this draws the table border  */ 
    background-color: rgb(66, 107, 107);
    overflow: hidden;
}

#table-head {
    background-color: rgb(54, 87, 87);
}

#table th:first-child {
    width: 60%;
    text-align: left;
    background-color: rgb(54, 87, 87);
}

#table th {
    padding: 5px;
    border: 2px solid rgb(27, 54, 54);
}
</style>