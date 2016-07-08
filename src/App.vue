<template>
    <h1>Poker app</h1>

    <div class="row">
        <div class="col-lg-8">
            <h1>Timer</h1>
            <poker-timer></poker-timer>

            <h1>Blind: <poker-blind></poker-blind></h1>

            <h1>Tokens</h1>
            <poker-tokens></poker-tokens>

            <h1>Winner <span class="btn btn-primary btn-raised" @click="showWinner = !showWinner">{{ showWinner ? '-' : '+' }}</span></h1>
            <div v-show="showWinner">
                <poker-winner></poker-winner>
            </div>
        </div>
        <div class="col-lg-4">
            <h1>Rules</h1>
            <img src="https://s-media-cache-ak0.pinimg.com/originals/92/a6/9e/92a69ea14fb0600a99a7322edc280ba8.gif" alt="" class="img-responsive">
        </div>
    </div>
</template>

<script>
    require("style!css!bootstrap/dist/css/bootstrap.css");
    require("style!css!bootstrap-material-design/dist/css/bootstrap-material-design.css");
    require("style!css!bootstrap-material-design/dist/css/ripples.css");

    require("script!jquery/dist/jquery.min.js");
    require("script!bootstrap-material-design/dist/js/material.min.js");
    require("script!bootstrap-material-design/dist/js/ripples.min.js");

    import PokerTimer from './components/Poker-timer.vue'
    import PokerWinner from './components/Poker-winner.vue'
    import PokerTokens from './components/Poker-tokens.vue'
    import PokerBlind from './components/Poker-blind.vue'

    export default {
        components: {
            PokerTimer, PokerWinner, PokerTokens, PokerBlind
        },
        data: function() {
            return {
                showWinner: false
            }
        },
        events: {
            'timer': function(timestamp) {
                console.log(timestamp);
                this.$broadcast('timer', timestamp);
            }
        }
    }

    $( document ).ready(function() {
        $.material.init();
    });
</script>

<style>

</style>
