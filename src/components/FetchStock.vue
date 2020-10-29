<template>
  <div class="container">
    <input @keypress="fetch_stock()" v-model="stock" placeholder="stock name" />
    <p>Fetching the stock {{ time }}</p>
    <p v-if="dst">{{ dst }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "FetchStock",
  data: function() {
    return {
      time: Date.now(),
      dst: [],
      stock: null,
      errors: null
    };
  },
  methods: {
    // fetch stock name returns data for that stock
    // next step display list of stock while typing
    fetch_stock: function() {
      //   fetch('https://www.alphavantage.co/query?function=OVERVIEW&symbol=IBM&apikey=demo').then(function(response) {
      //       if (response.status == 200) {
      //           return Promise.resolve(response.json())
      //       }
      //       return Promise.reject(response)
      //   }).then(function(d){
      //       console.log(d, d.Name)
      //       if (this.dst) {
      //           this.dst = d
      //       }
      //   })
      let url =
        "https://www.alphavantage.co/query?function=SYMBOL_SEARCH&keywords=" +
        this.stock +
        "&apikey=demo";
      axios
        .get(url)
        .then(response => {
          this.dst = JSON.stringify(response.data, null, 2);
        })
        .catch(err => {
          this.errors = err;
        });
    }
  }
};
</script>
