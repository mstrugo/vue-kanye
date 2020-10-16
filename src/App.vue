<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col">
        <button type="button" @click="getQuote" class="btn btn-outline-primary">Request Quote</button>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <div class="col-md-6" v-for="q in quotes" :key="q.id">
          <QuoteComponent :quote="q.quote" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { API_ENDPOINT } from './constants';
import QuoteComponent from './components/Quote';

export default {
  name: 'App',
  components: {
    QuoteComponent,
  },
  data() {
    return {
      quotes: [],
      fetching: false,
      error: '',
    };
  },
  methods: {
    getQuote() {
      fetch(API_ENDPOINT)
        .then(response => response.json())
        .then(res => {
          this.quotes.push({
            quote: res.quote,
            id: Date.now(),
          });
        })
        .catch(err => (this.error = err));
    },
    removeQuote(quoteId) {
      if (!quoteId) {
        this.quotes = [];
        return;
      }

      this.quotes = this.quotes.filter(q => q.id !== quoteId);
      return;
    },
  },
};
</script>
