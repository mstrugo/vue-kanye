<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col">
        <button type="button" @click="getQuote" class="btn btn-outline-primary">Request Quote</button>
        <button type="button" @click="removeQuote()" class="btn btn-outline-danger">Delete all</button>
      </div>
    </div>
    <div class="row">
      <div class="col-md-3" v-for="quote in quotes" :key="quote.id">
        <QuoteComponent :data="quote" @removeHandler="removeQuote" />
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
