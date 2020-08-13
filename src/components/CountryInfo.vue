<template>
    <div class="container">
      <p>{{ selectedCountry}}</p>
    </div>
</template>

<script>


export default {
    name: "CountryInfo",
    data() {
        return {
            selectedCountry: "",
            selectedState: "",
            selectedCity: ""
        }
    }
}
</script>

<style scoped>
    .container {
        background: #fefefe;
        padding: 40px;
        box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
    }
</style>