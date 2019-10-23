<template>
  <div>
    <h1>Countries</h1>
    <div>
      <countries-list :countries="countries"></countries-list>

    </div>
  </div>

</template>

<script>
import CountriesList from "./components/CountriesList.vue";
import {eventBus} from "./main.js"


export default {
  name: "app",
  data(){
    return{
      countries: [],
      selectedCountry: null
    };

  },
  mounted(){
    eventBus.$on("country-selected", (country) => {
      this.selectedCountry = country;
    });

    fetch("https://restcountries.eu/rest/v2/all")
    .then(response => response.json())
    .then(countries => this.countries = countries)
  },
  components: {
    "countries-list": CountriesList
  }
}
</script>

<style lang="css" scoped>
</style>
