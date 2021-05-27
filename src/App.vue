<template>
  <Header />
  <div class="container">
    <Home />
  </div>
</template>

<script>
import Header from "./components/Header";
import Home from "./views/Home";
export default {
  components: {
    Header,
    Home,
  },
};
</script>
<style scoped>
.container {
  width: 90%;
  margin: auto;
}
</style>