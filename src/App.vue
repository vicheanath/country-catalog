<template>
  <div class="app">
    <h1>Country Catalog</h1>
    <div class="search-bar">
      <input v-model="searchQuery" type="text" placeholder="Search by Country Name" />
      <button @click="search">Search</button>
    </div>
    <div class="sorting">
      <label>Sort by Country Name:</label>
      <select v-model="sortOrder" @change="sort">
        <option value="asc">Ascending</option>
        <option value="desc">Descending</option>
      </select>
    </div>
    <div class="catalog">
      <country-card v-for="country in filteredCountries" :key="country.cca2" :country="country" />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import CountryCard from './components/CountryCard.vue'

export default {
  components: {
    CountryCard
  },
  data() {
    return {
      countries: [],
      searchQuery: '',
      sortOrder: 'asc'
    }
  },
  mounted() {
    this.fetchCountries()
  },
  methods: {
    fetchCountries() {
      axios
        .get('https://restcountries.com/v3.1/all')
        .then((response) => {
          console.log(response.data)
          this.countries = response.data
        })
        .catch((error) => {
          console.error(error)
        })
    },
    search() {
      
    },
    sort() {
      // Sort filteredCountries based on sortOrder (asc or desc)
    }
  },
  computed: {
    filteredCountries() {
      // Return filtered and sorted countries based on searchQuery and sortOrder
      // You can implement the filtering and sorting logic here
      return this.countries
    }
  }
}
</script>

<style>
.app {
  margin: 0 auto;
  max-width: 1200px;
  padding: 20px;
}

h1 {
  text-align: center;
}

.search-bar {
  margin-bottom: 10px;
}

.catalog {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 20px;
}

.sorting {
  margin-bottom: 10px;
}

button {
  outline: none;
  border: none;
  background-color: #ccc;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
}

input {
  padding: 5px 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
  margin-right: 10px;
}

select {
  padding: 5px 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
  margin-left: 10px;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu,
    Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>
