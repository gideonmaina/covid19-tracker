<template>
  <div class="grid md:grid-cols-2 gap-4">
    <!-- Box 1 -->
    <div class="shadow-md bg-blue-100 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">New:</span>
        {{ commaSeparate(stats.NewConfirmed) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{ commaSeparate(stats.TotalConfirmed) }}
      </div>
    </div>
    <!-- Box 2 -->
    <div class="shadow-md bg-red-100 p-10 text-center rounded">
      <h3 class="text-3xl text-red-900 font-bold mb-4">Deaths</h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">New:</span>
        {{ commaSeparate(stats.NewDeaths) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{ commaSeparate(stats.TotalDeaths) }}
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "DataBoxes",
  props: ["stats"],
  methods: {
    commaSeparate(number) {
      return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>