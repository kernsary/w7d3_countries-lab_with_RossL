<template lang="html">
  <div>
    <label for="country-select">Select a Country</label>
    <select id="country-select" @change="handleChange" v-model="selectedCountry">
      <option v-for="country in countries" :value="country">{{country.name}}</option>
    </select>
    <!-- <ul>
    <list-item v-for="(country, index) in countries"
    :country="country"
    :key="index">
  </list-item>
</ul> -->
</div>
</template>

<script>
import ListItem from "./ListItem.vue";
import {eventBus} from "../main.js"

export default {
  name: "countries-list",
  data(){
    return{
      selectedCountry: null
    }
  },
  props: ["countries"],
  methods: {
    handleChange(){
      eventBus.$emit('country-selected', this.selectedCountry);
    }
  },
  components: {
    "list-item": ListItem
  }

}
</script>

<style lang="css" scoped>
</style>
