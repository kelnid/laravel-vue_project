<template>
    <div>
        <CreateComponent></CreateComponent>
        <IndexComponent></IndexComponent>
    </div>
</template>

<script>
import CreateComponent from "./components/CreateComponent";
import IndexComponent from "./components/IndexComponent";

export default {
    name: "App",

    data() {
        return {
            persons: null
        }
    },

    mounted() {

    },

    methods: {

    },

    components: {
        CreateComponent,
        IndexComponent,
    }
}
</script>

<style scoped>

</style>
