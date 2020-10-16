<template>
  <div class="card text-white bg-primary mb-3">
    <div class="card-header">
      Quote
      <button type="button" class="btn btn-outline-dark" @click="remove(data.id)">X</button>
    </div>
    <div class="card-body">
      <h5 class="card-title">{{ data.quote }}</h5>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Quote',
  props: {
    data: {
      quote: String,
      id: Number,
    },
  },
  methods: {
    remove(id) {
      this.$emit('removeHandler', id);
    },
  },
};
</script>
