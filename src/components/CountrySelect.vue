<template>
  <select
    @change="onCountrySelect()"
    v-model="selected"
    class="w-8/12 rounded m-10 form-select border py-2 bg-gray-700 text-white pl-3"
  >
    <option value="0">View by country</option>
    <option v-for="country in countries" :value="country.ID" :key="country.ID">
      {{ country.Country }}
    </option>
  </select>
</template>

<script>
export default {
  name: "CountrySelect",
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onCountrySelect() {
      const country = this.countries.find((item) => item.ID === this.selected);
      console.log(country);
      this.$emit("get-country", country);
    },
  },
};
</script>

<style>
</style>