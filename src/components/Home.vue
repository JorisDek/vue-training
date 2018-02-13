<template>
    <div>
        <card v-for="currency in currencies" @added="addCurrency">
            <template slot="currency_id">{{ currency.id }}</template>
            <template slot="currency_name">{{ currency.fullName }}</template>
        </card>
    </div>
</template>

<script>
import Card from './Card'
import axios from 'axios'

axios.defaults.headers.common['Access-Control-Allow-Origin'] = '*'

export default {
  name: 'Home',
  components: {
    Card
  },
  data () {
    return {
      currencies: [],
      storedCurrencies: []
    }
  },
  created: function () {
    // ajax request
    axios.get('https://api.hitbtc.com/api/2/public/currency')
      .then(({data}) => this.currencies = data)

    axios.get('https://api.hitbtc.com/api/2/public/ticker/')
      .then(({data}) => this.tickers = data)
  },
  methods: {
    addCurrency () {
      alert('add this currency')
    }
  }
}
</script>
