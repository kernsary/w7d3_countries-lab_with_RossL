<template lang="html">
  <div v-if="country">
    <h3>{{country.name}}</h3>
    <img id="flag" :src="country.flag" :alt="country.name">
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
    <p>Languages:</p>
    <ul>
      <li v-for="language in country.languages">{{language.name}}</li>
    </ul>
    </div>
</template>

<script>
export default {
  name: "country-detail",
  props: ["country"]
}
</script>

<style lang="css" scoped>

#flag {
  width: 60px;
}

</style>
