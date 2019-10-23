<template lang="html">
  <div>
    <form v-on:submit.prevent>
      <input type="text" placeholder="Search for a country ..." v-on:keyup="handleSearch" v-model="search">
      <!-- <label for="country-select">Select a Country</label> -->
      <select id="country-select" @change="handleChange" v-model="selectedCountry">
        <option disabled value="">Select a country</option>
        <option v-for="country in countries" :value="country">{{country.name}}</option>
      </select>
    </form>
    <!-- <ul>
    <list-item v-for="(country, index) in countries"
    :country="country"
    :key="index">
  </list-item>
</ul> -->
</div>
</template>

<script>
// import ListItem from "./ListItem.vue";
import {eventBus} from "../main.js"

export default {
  name: "countries-list",
  data(){
    return{
      search: "",
      selectedCountry: null
    }
  },
  props: ["countries"],
  methods: {
    handleSearch(){
      let foundCountry = this.countries.find((country) => {
        return country.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1
      })
      this.selectedCountry = foundCountry;
      eventBus.$emit('country-selected', this.selectedCountry);
    },

    handleChange(){
      eventBus.$emit('country-selected', this.selectedCountry);
    }
    // ,
    // components: {
    //   "list-item": ListItem
    // }

  }
}
</script>

<style lang="css" scoped>
</style>
