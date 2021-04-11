<template>
<div>
    <p v-if="category.name">{{category.name}}</p>
</div>
</template>

<script>

export default {
    props: ['category'],
    data() {
        return {
            category: []
            }
        },
    };
</script>

<style>

</style>
