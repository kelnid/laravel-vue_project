<template>
    <div>
        <table class="table">
            <thead>
            <tr>
                <th scope="col">#</th>
                <th scope="col">Name</th>
                <th scope="col">Age</th>
                <th scope="col">Job</th>
                <th scope="col">Edit</th>
                <th scope="col">Delete</th>
            </tr>
            </thead>
            <tbody>
                <template v-for="person in people">
                    <ShowComponent :person="person"></ShowComponent>
                    <EditComponent :person="person" :ref="`edit_${person.id}`"></EditComponent>
                </template>
            </tbody>
        </table>
    </div>
</template>

<script>
import EditComponent from "./EditComponent";
import ShowComponent from "./ShowComponent";
export default {
    name: "IndexComponent",

    data() {
        return {
            people: null,
            editPersonId: null,
            name: null,
            age: null,
            job: null,
        }
    },

    mounted() {
        this.getPeople()
    },

    methods: {
        getPeople() {
            axios.get('/api/people')
                .then(res =>{
                    this.people = res.data
                })
        },

        updatePerson(id) {
            this.editPersonId = null
            axios.patch(`/api/people/${id}`, {name: this.name,age: this.age,job: this.job}) //согласно полям в UpdateRequest
                .then(res =>{
                    this.getPeople()
                })
        },

        deletePerson(id) {
            axios.delete(`/api/people/${id}`)
                .then(res =>{
                    this.getPeople()
                })
        },

        changeEditPersonId(id, name, age, job) {
            this.editPersonId = id;
            let editName = `edit_${id}`
            this.$refs[editName][0].name = name
            this.$refs[editName][0].age = age
            this.$refs[editName][0].job = job
        },

        isEdit(id) {
            return this.editPersonId === id
        },
    },
    components: {
        EditComponent,
        ShowComponent,
    }
}
</script>

<style scoped>

</style>
