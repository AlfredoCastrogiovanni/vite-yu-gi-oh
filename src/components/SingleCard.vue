<script>
    export default {
    name: "SingleCard",
    props: {
        card: {
            type: Object,
            required: true
        }
    }
    }
</script>

<template>
    <div class="card col-12 col-md-4 col-lg-2 mb-4 me-3">
        <img :src="card.card_images[0].image_url" class="img-fluid mt-2" :alt=" card.name + '\'s card'">
        <div class="card-body">
            <h5 class="card-title">{{ card.name }}</h5>
            <p class="card-text">{{ card.archetype }}</p>
        </div>
    </div>
</template>

<style lang="scss" scoped>

</style>