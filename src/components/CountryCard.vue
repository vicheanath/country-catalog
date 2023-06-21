<template>
  <div class="card">
    <div class="hearder">
        <img :src="country.flags.png" alt="Flag" class="flag" />
        <h2>{{ country.name.official }}</h2>
    </div>
    

    <div class="details">

      <div class="data">
        <table>
          <tr>
            <th>Capital</th>
            <td>{{ country.capital.join(', ') }}</td>
          </tr>
          <tr>
            <th>Region</th>
            <td>{{ country.region }}</td>
          </tr>
          <tr>
            <th>Subregion</th>
            <td>{{ country.subregion }}</td>
          </tr>
          <tr>
            <th>Population</th>
            <td>{{ country.population }}</td>
          </tr>
          <tr>
            <th>Area</th>
            <td>{{ country.area }}</td>
          </tr>
          <tr>
            <th>Native Name</th>
            <td>
              {{ country.name.nativeName?.eng?.official }} ({{
                country.name.nativeName?.eng?.common
              }})
            </td>
          </tr>
          <tr>
            <th>Alternative Name</th>
            <td>{{ country.altSpellings[0] }}</td>
          </tr>
          <tr>
            <th>Calling Code</th>
            <td>{{ country?.idd.root }}</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['country'],
  methods: {
    showModal(country) {}
  }
}
</script>

<style scoped>

.hearder{
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
    width: 100%;
    text-align: left;
}
.card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 10px;
  cursor: pointer;
}

.flag {
  width: 100px;
  height: 60px;
  margin-right: 20px;
}

.details {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;
  width: 100%;
}

table {
  width: 100%;
}

th {
  text-align: left;
  padding-right: 10px;
}

td {
  text-align: left;
  padding-right: 10px;
}

.data {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-start;
  width: 100%;
}
</style>
