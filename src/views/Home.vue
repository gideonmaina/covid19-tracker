<template>
  <main v-if="!loading">
    <DataTitle :titleText="title" :dataDate="dataDate" />
    <div class="flex justify-center items-center">
      <CountrySelect :countries="countries" @get-country="getCountryData" />
      <button
        v-if="stats.Country"
        @click="getGlobalData"
        class="p-3 text-3xl text-white rounded focus:outline-none bg-blue-700 w-4/12"
      >
        Global Stats
      </button>
    </div>
    <DataBoxes :stats="stats" />
  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl ml-10">Fetching data ...</div>
  </main>
</template>

<script>
import DataTitle from "@/components/DataTitle";
import DataBoxes from "@/components/DataBoxes";
import CountrySelect from "@/components/CountrySelect";
export default {
  name: "Home",
  components: { DataTitle, DataBoxes, CountrySelect },
  data() {
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      stats: {},
      countries: {},
    };
  },
  methods: {
    async fetchCovidata() {
      const res = await fetch("https://api.covid19api.com/summary");
      const data = await res.json();
      return data;
    },
    getCountryData(country) {
      this.stats = country;
      this.title = country.Country;
    },
    async getGlobalData() {
      this.loading = true;
      const data = await this.fetchCovidata();
      this.title = "Global";
      this.stats = data.Global;
      this.loading = false;
    },
  },
  async created() {
    const data = await this.fetchCovidata();
    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
    // console.log(data);
  },
};
</script>
