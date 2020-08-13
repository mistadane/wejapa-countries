<template>
  <div id="app">
    <Header />
    <div class="main">
      <div class="country-grid">
        <Countries />
        <CountryInfo />
     </div>
    </div> 
  </div>
</template>

<script>

import Header from './components/Header';
import Countries from './components/Countries';
import CountryInfo from './components/CountryInfo';

export default {
  name: 'App',
  components: {
    Header,
    Countries,
    CountryInfo
  }
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  }

  body {
    background-image: url('./assets/map.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    overflow-y: hidden;
  }

  .main {
    width: 100%;
    background: rgba(6, 7, 8, .7);
    padding: 50px;
    height: 100vh;
  }

  .country-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-column-gap: 50px;
    max-width: 960px;
    margin: 50px auto;
  }
</style>
