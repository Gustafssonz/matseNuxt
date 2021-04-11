<template>
<div>
    <p>{{category}}</p>
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
