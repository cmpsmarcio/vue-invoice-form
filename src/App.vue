<template>
  <div id="app">
    <InvoiceForm />
  </div>
</template>

<script>
import InvoiceForm from "./components/InvoiceForm.vue";

export default {
  name: "app",
  components: {
    InvoiceForm
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
