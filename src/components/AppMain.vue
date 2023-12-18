<script>
    import Listcards from './Listcards.vue';
    import axios from 'axios';

    export default {
        name: "AppMain",
        components: {
            Listcards
        },
        data() {
            return {
                cardsList: []
            }
        },
        methods: {
            getcardList() {
                axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php', {
                    params: {
                    num: 4000,
                    offset: 0
                    }
                })
                .then( response => {
                    console.log(response);
                    this.cardsList = response.data.data;
                })
                .catch(function (error) {
                    console.log(error);
                });
            }
        },
        created() {
            this.getcardList()
        }
    }
</script>

<template>
    <Listcards :cardsList="cardsList"/>
</template>

<style lang="scss" scoped>

</style>