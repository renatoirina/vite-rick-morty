<script>
export default {
    props: {
        cardObject: Object,
    }
}
</script>

<template>
    <div class="p2 py-1">
        <img :src="cardObject.image" class="img-fluid rounded-circle border-0" :alt="cardObject.name">
        <span class="text-center d-block pt-3 fs-5">{{ cardObject.name }}</span>
        <span class="text-center d-block fs-6">{{ cardObject.status }}</span>
        <span class="text-center d-block fs-6 pb-4">{{ cardObject.species }}</span>
    </div>
</template>

<style>
.rounded-circle {
    box-shadow: 0px 0px 10px black;
}
</style>
