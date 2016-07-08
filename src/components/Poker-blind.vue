<template>
    <div class="form-inline label-floating">
        <input type="number" v-model="small" class="form-control">/
        <input type="number" v-model="big" class="form-control">
    </div>
</template>

<style>
</style>

<script>
    export default {
        data () {
            return {
                small: 50,
                big: 100
            }
        },
        events: {
            'timer': function(timestamp) {
                if (timestamp % (30 * 60) == 0) {
                    this.small *= 2;
                    this.big *= 2;
                }
            }
        }
    }
</script>