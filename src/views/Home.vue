<template>
  <div class="home">
    <Header />
    <FetchStock />
    <Footer />
  </div>
</template>

<script>
// @ is an alias to /src
import Header from "@/components/Header.vue";
import FetchStock from "@/components/FetchStock.vue";
import Footer from "@/components/Footer.vue";
export default {
  name: "home",
  components: {
    Header,
    FetchStock,
    Footer
  }
};
</script>
