<script>
    import SingleCard from './SingleCard.vue';

    export default {
        name: "ListCards",
        components: {
            SingleCard
        },
        props: {
            cardsList: {
                type: Object,
                required: true
            }
        }
    }
</script>

<template>
    <div class="container">
        <div class="row justify-content-center" v-if="cardsList.length >= 20">
            <SingleCard v-for="card in cardsList" :card="card"/>
        </div>
        <div v-else class="d-flex justify-content-center align-items-center">
            <span class="fs-1 mt-5">Loading</span>
        </div>
    </div>
</template>

<style lang="scss" scoped>

</style>
