<template>
    <form @submit.prevent="addJeton" class="form-inline">
        <div class="form-group label-floating">
            <label for="form-color" class="control-label">Color</label>
            <input type="text" v-model="color" v-el:color-input class="form-control" id="form-color">
        </div>
        <div class="form-group label-floating">
            <label for="form-value" class="control-label">Value</label>
            <input type="number" v-model="value" class="form-control" id="form-value">
        </div>
        <button class="btn btn-primary btn-raised">Add</button>
    </form>
    <ul id="jetons">
        <li v-for="(index, jeton) in jetons">
            {{ jeton.color }}: {{ jeton.value }}
            <button @click="remove(index)" class="btn btn-danger btn-raised">X</button>
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
                });
                this.$els.colorInput.focus();
                this.$els.colorInput.select();
            },
            remove: function(index) {
                this.jetons.splice(index, 1);
            }
        }
    }
</script>