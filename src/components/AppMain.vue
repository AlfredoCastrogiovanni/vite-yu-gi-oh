<script>
    import ListCards from './ListCards.vue';
    import AppSearch from './AppSearch.vue';
    import axios from 'axios';

    export default {
        name: "AppMain",
        components: {
            ListCards,
            AppSearch
        },
        data() {
            return {
                cardsList: []
            }
        },
        methods: {
            getCardList(archetype) {
                axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php', {
                    params: {
                    num: 4000,
                    offset: 0,
                    archetype: archetype
                    }
                })
                .then( response => {
                    console.log(response);
                    this.cardsList = response.data.data;
                })
                .catch(function (error) {
                    console.log(error);
                });
            },
            selectArchetype(archetype) {
                this.getCardList(archetype);
            }
        },
        created() {
            this.getCardList();
        }
    }
</script>

<template>
    <AppSearch @search="selectArchetype"/>
    <Listcards :cardsList="cardsList"/>
</template>

<style lang="scss" scoped>

</style>