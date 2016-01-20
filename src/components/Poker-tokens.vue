<template>
    <ul id="jetons">
        <form @submit.prevent="addJeton">
            Color: <input type="text" v-model="color">
            Value: <input type="number" v-model="value">
            <input type="submit" value="Add">
        </form>

        <li v-for="(index, jeton) in jetons">
            {{ jeton.color }}: {{ jeton.value }}
            <button @click="remove(index)">X</button>
        </li>
    </ul>
</template>

<style>

</style>

<script>
    export default{
        data(){
            return {
                jetons: [
                    {
                        value: 10,
                        color: 'blue'
                    }
                ],
                color: 'blue',
                value: 20
            }
        },
        methods: {
            addJeton: function() {
                this.jetons.push({
                    value: this.value,
                    color: this.color
                })
            },
            remove: function(index) {
                this.jetons.splice(index, 1);
            }
        }
    }
</script>