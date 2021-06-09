<template>
  <!-- <select  @change="onChange()" v-model="selected" class="form-select mt-1 block w-full border p-3 rounded mt-10 focus:outline-none appearance-none">
    <option value="0">Select Country</option>
    <option v-for="country in countries" :value="country.ID">{{ country.Country }}</option>
  </select> -->
  <multiselect
      @select="onChange"
      placeholder="Select or Search a Country"
      v-model="value"
      :options="options"
      :max-height="70"
      :open-direction="top"
      :show-labels="ok"
      class="mt-1 mb-10 md:mb-0 block w-full border text-lg rounded mt-10 font-bold"
      >
    </multiselect>
</template>

<script>
import Multiselect from 'vue-multiselect'

  export default {
    name: 'CountrySelect',
    components: {
      Multiselect,
    },
    props: ['countries'],
    data() {
      return {
        value: '',
        options: [],
      }
    },
    methods: {
      onChange(optionName) {
        const country = this.countries.find((item) => item.Country === optionName)
        console.log('country is', country)
        this.$emit('get-country', country)
      }
    },
      created() {
      const countriesName = this.countries.map((country) => country.Country)

      this.options = countriesName
    },
  }
</script>

<style>
.multiselect__tags {
  padding: 10px;
}
.multiselect__content-wrapper {
  overflow: scroll;
}
.multiselect__content {
  width: 100%;
  padding: 0;
}
.multiselect__element {
  padding: 10px;
}
.multiselect__option span {
  width: 100% !important
}
.multiselect__element:hover {
  background-color: #f8f9fa;
}
.multiselect__input {
  outline: none;
}
</style>

