<template>
    <div class="container">
        <div class="columns">
            <div class="column">
                <article class="message" v-for="ticker in tickers">
                    <div class="message-header">
                        <p>{{ ticker.symbol }}</p>
                    </div>
                    <div class="message-body">
                        Ask: {{ ticker.ask }}
                    </div>
                </article>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
axios.defaults.headers.common['Access-Control-Allow-Origin'] = '*'

export default {
  data () {
    return {
      tickers: []
    }
  },
  created: function () {
    // ajax request
    axios.get('https://api.hitbtc.com/api/2/public/ticker')
      .then(({data}) => this.tickers = data)
  }
}
</script>
