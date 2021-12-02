<template>
  <div id="app">
    <comHeader />
    <comMainSection />
    <h3 class="text-danger">Informations: </h3>
    <comSearch :infoes="names"/>
  </div>
</template>

<script>
import comHeader from "./components/Header/Header.vue";
import comSearch from "./components/Search/Search.vue";
import comMainSection from "./components/MainSection/MainSection.vue";

export default {
  data() {
    return {
      names: ["Mueem", "Nahid", "Dhaka", "Bangladesh"]
    };
  },
  components: {
    comHeader,
    comSearch,
    comMainSection
  },
};
</script>

<style>
body {
  font-family: "Lora", serif;
}
</style>