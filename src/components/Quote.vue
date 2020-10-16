<template>
  <div class="card text-white bg-primary mb-3">
    <div class="card-header">Quote</div>
    <div class="card-body">
      <h5 class="card-title">{{ quote }}</h5>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Quote',
  props: {
    quote: String,
  },
};
</script>

<style scoped>
/*
.card--width {
  max-width: 100;
}
*/
</style>
