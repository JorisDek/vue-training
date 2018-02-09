<template>
    <div class="container">
        <div class="columns">
            <div class="column">
                <h2>All currencies</h2>
                <table class="table">
                    <thead>
                        <tr>
                            <td>Name</td>
                            <td>Fullname</td>
                            <td></td>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="currency in currencies">
                            <td>{{ currency.id }}</td>
                            <td>{{ currency.fullName }}</td>
                            <td class="is-hidden">
                                <input type="text" name="currency_id" :value="currency.id">
                            </td>
                            <td>
                                <button class="button is-success" @click.once="addCurrency">Add</button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div class="column">
                <h2>Watched currencies</h2>
                <div class="tabs is-boxed">
                    <ul>
                        <li class="is-active">
                            <a>BTC</a>
                        </li>
                        <li>
                            <a>ETH</a>
                        </li>
                    </ul>
                </div>
                <div class="tab-content">
                <table class="table is-striped">
                        <thead>
                            <tr>
                                <td>Name</td>
                                <!--<td></td>-->
                            </tr>
                        </thead>
                        <tbody>
                            <tr v-for="currency in stored_currencies">
                                <td>{{ currency.id }}</td>
                                <!--<td></td>-->
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
        <!--<div class="columns is-multiline is-mobile">-->
            <!--<div class="column is-one-fifth" v-for="ticker in tickers">-->
                <!--<article class="message">-->
                    <!--<div class="message-header">-->
                        <!--<p>{{ ticker.symbol }}</p>-->
                    <!--</div>-->
                    <!--<div class="message-body">-->
                        <!--Bid: {{ ticker.bid }}-->
                    <!--</div>-->
                <!--</article>-->
            <!--</div>-->
        <!--</div>-->
    </div>
</template>

<script>
import axios from 'axios'
// axios.defaults.headers.common['Access-Control-Allow-Origin'] = '*'

export default {
  data () {
    return {
      currencies: [],
      tickers: [],
      stored_currencies: [],
      newCurrency: ''
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
      this.stored_currencies.push(this.newCurrency)
    }
  },
  mounted () {

  }
}
</script>
