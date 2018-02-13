<template>
    <div class="card">
        <div class="card-content">
            <p class="title">
                <slot name="currency_id"></slot>
            </p>
            <p class="subtitle">
                <slot name="currency_name"></slot>
            </p>
        </div>
        <footer class="card-footer">
            <!--<p class="card-footer-item">-->
                <!--<span>-->
                    <!--View on <a href="https://twitter.com/codinghorror/status/506010907021828096">Twitter</a>-->
                <!--</span>-->
            <!--</p>-->
            <p class="card-footer-item">
                <button class="button is-success" @click="addToList($event)" :id="id">Add</button>
            </p>
        </footer>
    </div>
</template>

<script>
export default {
  name: 'card',
  props: [
    'id',
    'name'
  ],
  methods: {
    addToList (e) {
      // this.$emit('added')
      console.log(e)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<!--<style scoped>-->

<!--</style>-->
