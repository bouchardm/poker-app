<template>
    <form v-show="!showWinner" @submit.prevent class="form-inline">
        <h3>With rebuy</h3>
        <div class="form-group label-floating">
            <label for="form-nbPerson" class="control-label">Number of person</label>
            <input type="number" v-model="nbPerson" class="form-control" id="form-nbPerson">
        </div>
        <div class="form-group label-floating">
            <label for="form-cashPerson" class="control-label">Cash by person</label>
            <input type="number" v-model="cashPerson" class="form-control" id="form-cashPerson">
        </div>

        <h3>Without rebuy</h3>
        <div class="form-group label-floating">
            <label for="form-nbPersonNoRebuy" class="control-label">Number of person</label>
            <input type="number" v-model="nbPersonNoRebuy" class="form-control" id="form-nbPersonNoRebuy">
        </div>
        <div class="form-group label-floating">
            <label for="form-cashPersonNoRebuy" class="control-label">Cash by person</label>
            <input type="number" v-model="cashPersonNoRebuy" class="form-control" id="form-cashPersonNoRebuy">
        </div>
    </form>

    <div class="poker-winner">
        <div id="total">
            Total: {{ total | currency }}
        </div>
        <div class="first">
            First: {{ first | currency }}
        </div>
        <div class="second">
            Second: {{ second | currency }}
        </div>
        <div class="third">
            Third: {{ third | currency }}
        </div>
    </div>
</template>

<style>

</style>

<script>
    export default{
        data() {
            return {
                showWinner: false,
                nbPerson: 4,
                cashPerson: 20,
                nbPersonNoRebuy: 4,
                cashPersonNoRebuy: 20
            }
        },
        computed: {
            total: function() {
                return (this.nbPerson * this.cashPerson) + (this.nbPersonNoRebuy * this.cashPersonNoRebuy);
            },
            first: function() {
                return this.total * 0.5;
            },
            second: function() {
                return this.total * 0.3;
            },
            third: function() {
                return this.total * 0.2;
            }
        },
    }
</script>