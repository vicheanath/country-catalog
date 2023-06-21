<template>
  <modal name="country-modal">
    <div class="modal-content">
      <h2>{{ country.name.official }}</h2>
      <img :src="country.flags.png" alt="Flag" class="flag" />
      <div class="details">
        <p>2 character Country Code: {{ country.cca2 }}</p>
        <p>3 character Country Code: {{ country.cca3 }}</p>
        <p>Native Country Name: {{ country.name.nativeName.eng }}</p>
        <p>Alternative Country Name: {{ country.altSpellings[0] }}</p>
        <p>Country Calling Codes: {{ country?.idd.root }}</p>
      </div>
    </div>
  </modal>
</template>

<script>
export default {
  props: ['country']
}
</script>

<style scoped>
.modal-content {
  padding: 20px;
}

.flag {
  width: 100px;
  height: 60px;
  margin-bottom: 10px;
}
</style>
