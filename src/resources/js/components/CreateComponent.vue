<template>
    <div class="w-25">
        <div class="mb-3">
            <input type="text" id="name" class="form-control" placeholder="name" v-model="name">
        </div>
        <div class="mb-3">
            <input type="number" id="age" class="form-control" placeholder="age" v-model="age">
        </div>
        <div class="mb-3">
            <input type="text" id="job" class="form-control" placeholder="job" v-model="job">
        </div>
        <div class="mb-3">
            <button class="btn btn-primary" @click.prevent="addPerson">Добавить</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "CreateComponent",

    data() {
        return {
            name: null,
            age: null,
            job: null,
        }
    },

    methods: {
        addPerson() {
            axios.post('/api/people', {name: this.name,age: this.age,job: this.job})
                .then(res => {
                    this.name = null
                    this.age = null
                    this.job = null
                })
        }
    }
}
</script>

<style scoped>

</style>
