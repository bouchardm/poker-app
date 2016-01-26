<template>
    <form action="" v-show=" ! timerStart" @submit.prevent class="form-inline">
        <div class="form-group label-floating">
            <label for="form-hours" class="control-label">Hours</label>
            <input type="number" v-model="hours" class="form-control" id="form-hours">
        </div>
        :
        <div class="form-group label-floating">
            <label for="form-minutes" class="control-label">Minutes</label>
            <input type="number" v-model="minutes" class="form-control" id="form-minutes">
        </div>
        :
        <div class="form-group label-floating">
            <label for="form-seconds" class="control-label">Minutes</label>
            <input type="number" v-model="seconds" class="form-control" id="form-seconds">
        </div>
        <button @click="toggleTimer" class="btn btn-primary btn-raised">Play</button>
    </form>

    <span class="h2" id="poker-timer" v-show="timerStart"></span>
    <button @click="toggleTimer" v-show="timerStart" class="btn btn-primary btn-raised">Pause</button>
</template>

<style>

</style>

<script>
    import $ from 'jquery'
    import 'jquery-countdown/src/countdown'

    export default {
        data () {
            return {
                timerStart: false,
                hours: 1,
                minutes: 30,
                seconds: 0,
                clock: null
            }
        },
        ready: function () {
            var $clock = $('#poker-timer');
            var that = this;
            this.clock = $clock.countdown(this.timeFrom(1, 30, 0), function (event) {
                $(this).html(event.strftime('%H:%M:%S'));
            }).on('update.countdown', function(event) {
                that.hours = event.strftime('%H');
                that.minutes = event.strftime('%M');
                that.seconds = event.strftime('%S');
            });
            this.clock.countdown('pause');
        },
        methods: {
            updateTimer: function() {
                this.clock.countdown(this.timeFrom(this.hours, this.minutes, this.seconds), function (event) {
                    $(this).html(event.strftime('%H:%M:%S'));
                });
            },
            toggleTimer: function () {
                this.updateTimer();
                this.clock.countdown(this.timerStart ? 'pause' : 'resume');
                this.timerStart = ! this.timerStart;
            },
            timeFrom: function (hours, minutes, seconds) {
                return new Date(new Date().valueOf() + hours * 60 * 60 * 1000 + minutes * 60 * 1000 + seconds * 1000);
            }
        }
    }
</script>