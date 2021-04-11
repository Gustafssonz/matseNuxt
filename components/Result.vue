<template>
<div>
  <div class="card text-left">
    <img class="card-img-top" :src="data.imageUrl" alt="">
    <div class="card-body">
      <h4 class="card-title">{{data.name}}</h4>
      <p class="card-text">{{data.content}}</p>
    </div>
  </div>
</div>

</template>

<script>
export default {
   props: ['data'],
    data() {
        return {
            products: [],
            }
        },
    };
</script>

<style>

</style>
