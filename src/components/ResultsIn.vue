<template>
    <p>Reaction Time = {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = 'Ninja Finger'
        } else if (this.score < 400) {
            this.rank =  'Rapid Reflex'
        } else {
            this.rank = 'Snail pace'
        }
    } 
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: rgb(11, 105, 73);
        font-weight: bold;
    }
</style>