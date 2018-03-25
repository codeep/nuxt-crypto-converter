<template>
  <div class="row" id="main-app">
    <div class="col-sm-5">
      <span>Convert From</span>
      <select class="form-control" v-model="from_value" v-on:change="change">
        <option v-for="crypto in cryptos" v-bind:key="crypto.id" v-bind:value="crypto.id">{{crypto.name}}</option>
      </select>
    <input type="number" name="from" class="form-control sm-6" placeholder="Enter Amount" v-model="from" v-on:keyup="change">
    </div>
    <div class="col-md-2">
      <img src="/images/two_way.png" class="app-two-way">
    </div>
    <div class="col-sm-5">
      <span>Convert To</span>
      <select class="form-control" v-model="to_value" v-on:change="change">
        <option v-for="crypto in cryptos" v-bind:key="crypto.id" v-bind:value="crypto.id">{{crypto.name}}</option>
      </select>
      <input type="number" name="to" class="form-control sm-6" id="to" placeholder="Enter Amount" v-model="to" v-on:keyup="change">
    </div>
  </div>
</template>

<style>
  .app-two-way {
    width: 2rem;
  }

  #main-app {
    margin-top: 3rem;
  }
</style>

<script>
  export default {
    data () {
      return {
        to_value: null,
        from_value: null,
        to: 0,
        from: 0,
        cryptos: [
          {
            "id": 1,
            "name": "Bitcoin",
            "price_usd": "8578.11", 
          }, {
            "id": 2,
            "name": "Ethereum", 
            "price_usd": "523.061",
          }, {
            "id": 3,
            "name": "Ripple", 
            "price_usd": "0.640147",
          }, {
            "id": 4,
            "name": "Litecoin", 
            "price_usd": "160.276",
          }, {
            "id": 5,
            "name": "EOS", 
            "price_usd": "6.59186",
          }
        ]
      }
    },
    methods: {
      change: function (event) {
        console.log(event.path[0].id)

        if(this.from_value && this.to_value) {
          if(event.path[0].id === "to" && this.to) {
            const from_price_usd = this.cryptos[this.from_value - 1].price_usd;
            const to_price_usd = this.cryptos[this.to_value - 1].price_usd;
            this.from = this.to/(from_price_usd / to_price_usd);
            return;
          }

          if(this.from) {
            const from_price_usd = this.cryptos[this.from_value - 1].price_usd;
            const to_price_usd = this.cryptos[this.to_value - 1].price_usd;

            this.to = this.from * (from_price_usd / to_price_usd)
          }
        }
      }
    }
  }
</script>

