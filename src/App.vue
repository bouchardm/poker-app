<template>
    <h1>Poker app</h1>

    <div class="row">
        <div class="col-lg-8">
            <h1>Timer</h1>
            <poker-timer></poker-timer>

            <h1>Tokens</h1>
            <poker-tokens></poker-tokens>

            <h1>Winner</h1>
            <poker-winner></poker-winner>
        </div>
        <div class="col-lg-4">
            <h1>Rules</h1>
            <img src="https://s-media-cache-ak0.pinimg.com/originals/92/a6/9e/92a69ea14fb0600a99a7322edc280ba8.gif" alt="">
        </div>
    </div>
</template>

<script>
    import PokerTimer from './components/Poker-timer.vue'
    import PokerWinner from './components/Poker-winner.vue'
    import PokerTokens from './components/Poker-tokens.vue'

    export default {
        components: {
            PokerTimer, PokerWinner, PokerTokens
        },
        data: function() {
            return {
                showWinner: false
            }
        }
    }
</script>

<style>

</style>
