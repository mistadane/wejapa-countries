<template>
    <div class="container">
      <div class="contain">
        <form action="">
            <div>
                <label for="countries">Country</label>
                <select name="countries" id="countries" v-model="selectedCountry" @change="countrySelect($event)">
                    <option value="" disabled selected hidden>Select a Country</option>
                    <option :value="country.name" :key="country.id" v-for="country in countries">{{ country.name }}</option>
                </select>
            </div>
            <div>
                <label for="states">State</label>
                <select name="states" id="" v-model="selectedState" @change="stateSelect($event)">
                    <option value="" disabled selected hidden>Select a State</option>
                    <option :value="state.name" :key="state.id" v-for="state in states">{{ state.name }}</option>
                </select>
                <div v-if="stateError" :class="{empty: stateError}">
                    <p>This country has no states. Kindly select another country</p>
                </div>
            </div>
            <div>
                <label for="cities">City</label>
                <select name="cities" id="" v-model="selectedCity">
                    <option value="" disabled selected hidden>Select a City</option>
                    <option :value="city.name" :key="city.id" v-for="city in cities">{{ city.name }}</option>
                </select>
                <div v-if="cityError" :class="{empty: cityError}">
                    <p>This state has no cities. Kindly select another state or country</p>
                </div>
            </div>
        </form>
      </div>
      <div class="contain">
        <div class="option">
          <h3>Selected Country</h3>
          <p>{{ selectedCountry }}</p>
        </div>
        <div class="option">
          <h3>Selected State</h3>
          <p>{{ selectedState }}</p>
        </div>
        <div class="option">
          <h3>Selected City</h3>
          <p>{{ selectedCity }}</p>
        </div>
      </div>   
    </div>
</template>

<script>

export default {
    name: "Countries",
    
    data() {
        return {
            selectedCountry: "",
            selectedState: "",
            selectedCity: "",
            countries: [],
            states: [],
            cities: [],
        }
    },
    
    
    mounted() {
        fetch("https://raw.githubusercontent.com/dr5hn/countries-states-cities-database/master/countries%2Bstates%2Bcities.json", {
            method: 'get'
        })
        .then((response) => {
            return response.json()
        })
        .then((jsonData) => {
            this.countries = jsonData;
        })
    },
    methods: {
        countrySelect(event){
            const state = event.target.value
            const index = this.countries.findIndex((x=>x.name === state))
            const countryState = this.countries[index]['states']
            if (countryState.length === 0){
                this.stateError = !this.stateError 
                this.states = ""   
                this.cities = ""
            } else{
                this.states = countryState
                this.stateError = false
            }
        },
        stateSelect(event){
            const state = event.target.value
            const index = this.states.findIndex((x=>x.name === state))
            const city = this.states[index]['cities']
            if (city.length === 0){
                this.cityError = !this.cityError
            }else{
                this.cities = city
                this.cityError = false
            }
        }
    }
    
}
</script>

<style scoped>
    .container {
      width: 100%;
      display: flex;
      justify-content: center;
    }
    .contain {
        width: 100%;
        background: #fefefe;
        padding: 40px;
        box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
        margin: 20px;
    }
    select {
        display: block;
        width: 100%;
        height: 40px;
        margin-bottom: 20px;
        border: 1px solid #e2e8f0;;
        border-radius: 5px;
    }
    label {
        display: block;
        font-weight: 600;
        font-size: 20px;
        margin-bottom: 10px;
    }
    .empty {
        color: red;
        font-size: 12px;
        position: relative;
        top: -10px
    }

    .option {
      margin-bottom: 50px;
    }

    p {
        font-size: 14px;
        color: #525569;
        padding: 5px;
    }

    @media only screen and (max-width: 320px) {
        .container {
            display: flex;
            flex-wrap: wrap;
        } 
    }

    @media only screen and (max-width: 375px) {
        .container {
            display: flex;
            flex-wrap: wrap;
        } 
    }

    @media only screen and (max-width: 414px) {
        .container {
            display: flex;
            flex-wrap: wrap;
        } 
    }

    @media only screen and (max-width: 768px) {
        .container {
            display: flex;
            flex-wrap: wrap;
        } 
    }

    
</style>

