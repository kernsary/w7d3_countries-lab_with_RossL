<template lang="html">

</template>

<script>
export default {
  name: "app",
  data(){
    return{
    countries: [],
    selectedCountry: null
  };

},
mounted(){
  fetch("https://restcountries.eu/rest/v2/all")
  .then(response => response.json())
  .then(countries => this.countries = countries)
}
}
</script>

<style lang="css" scoped>
</style>
