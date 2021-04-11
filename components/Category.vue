<template>
<div>
    <p v-if="data.name">{{data.name}}</p>
</div>
</template>

<script>

export default {
    props: ['data'],
    data() {
        return {
            category: []
            }
        },
    };
</script>

<style>

</style>
