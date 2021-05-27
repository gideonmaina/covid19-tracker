<template>
  <div class="flex flex-col align-center justify-center text-center mt-6 mb-6">
    <h1 class="text-3xl">{{ titleText }}</h1>
    <p>{{ timestamp }}</p>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "DataTitle",
  props: ["titleText", "dataDate"],
  computed: {
    timestamp: function () {
      return moment(this.dataDate).format("MMMM Do YYYY, hh:mm:ss a");
    },
  },
};
</script>
