<script>
import CardsComponent from "./CardsComponent.vue";

export default {
    components: {
        CardsComponent,
    },
    props: {
        charactersArray: Array,
    }
}

</script>

<template>
    <div class="container">
        <div class="row">
            <div class="col-3 px-6"  v-for="elem in charactersArray">
                <CardsComponent :cardObject="elem" />
            </div>
        </div>
    </div>
</template>

<style>

</style>