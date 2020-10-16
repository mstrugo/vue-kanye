<template>
  <div class="card text-white mb-3" :class="randomizedBg">
    <div class="card-header">
      Quote
      <button type="button" class="close" @click="remove(data.id)" aria-label="Close">
        <span aria-hidden="true">&times;</span>
      </button>
    </div>
    <div class="card-body">
      <h5 class="card-title">{{ data.quote }}</h5>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Quote',
  data() {
    return {
      colors: ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark'],
    };
  },
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
  computed: {
    randomizedBg() {
      const index = Math.floor(Math.random() * this.colors.length);
      const color = this.colors[index] || this.colors[0];

      return `bg-${color}`;
    },
  },
};
</script>
