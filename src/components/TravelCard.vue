<template id="placeCard">
 <div class="place">
    <img :src="card.img" width="235" height="300"/>
    <h2>{{ card.name }}</h2>
    <p>{{ card.desc }}</p>
 </div>
</template>

<script>
    export default {
        name: 'TravelCard',
        props: {
            card: Object
        }
    }
</script>

<style>

</style>