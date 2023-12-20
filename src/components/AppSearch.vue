<script>
    import axios from 'axios';

    export default {
    name: "AppSearch",
    data() {
        return {
            archetypeList: [],
            selectedArchetype: "",
        }
    },
    methods: {
        getArchetypeList() {
            axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
            .then( response => {
                console.log(response);
                this.archetypeList = response.data;
            })
            .catch(function (error) {
                console.log(error);
            });
        }
    },
    created() {
        this.getArchetypeList();
    }
    }
</script>

<template>
    <div class="container mb-3">
        <div class="row">
            <select class="form-select" v-model="selectedArchetype" @change="$emit('search', selectedArchetype)">
                <option v-for="archetype in archetypeList" :value="archetype.archetype_name">{{ archetype.archetype_name }}</option>
            </select>
        </div>
    </div>
</template>

<style lang="scss" scoped>

</style>