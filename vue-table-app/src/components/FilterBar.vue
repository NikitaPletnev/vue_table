<template>
  <div class="filter-bar">
    <div class="filter">
      <label for="country-select">Country</label>
      <select id="country-select" v-model="localFilterCountries" @change="onCountryChange">
        <option value="">All Countries</option>
        <option v-for="country in countries" :key="country" :value="country">{{ country }}</option>
      </select>
    </div>
    <div class="filter">
      <label for="company-select">Company</label>
      <select id="company-select" v-model="localFilterCompanies" @change="onCompanyChange">
        <option value="">All Companies</option>
        <option v-for="company in companies" :key="company" :value="company">{{ company }}</option>
      </select>
    </div>
    <div class="filter">
      <label for="policy-select">Policy</label>
      <select id="policy-select" v-model="localFilterPolicy" @change="onPolicyChange">
        <option value="">All Policies</option>
        <option v-for="policy in policies" :key="policy" :value="policy">{{ policy }}</option>
      </select>
    </div>
    <div class="actions">
      <button @click="clearFilters">Clear Filters</button>
    </div>
  </div>
</template>


<script setup lang="ts">
import { ref, watch, defineEmits, defineProps } from 'vue';

const emit = defineEmits(['handleFilter', 'handleClearFilter', 'updateFilter']);

const props = defineProps({
  filterCountries: String,
  filterCompanies: String,
  filterPolicy: String,
});

const localFilterCountries = ref(props.filterCountries);
const localFilterCompanies = ref(props.filterCompanies);
const localFilterPolicy = ref(props.filterPolicy);

watch(() => props.filterCountries, (newVal) => { localFilterCountries.value = newVal; });
watch(() => props.filterCompanies, (newVal) => { localFilterCompanies.value = newVal; });
watch(() => props.filterPolicy, (newVal) => { localFilterPolicy.value = newVal; });

const onCompanyChange = (event: Event) => {
  const selectedValue = (event.target as HTMLSelectElement).value;
  emit('handleFilter', 'companies', selectedValue);
};

const onPolicyChange = (event: Event) => {
  const selectedValue = (event.target as HTMLSelectElement).value;
  emit('handleFilter', 'policy', selectedValue);
};

const onCountryChange = (event: Event) => {
  const selectedValue = (event.target as HTMLSelectElement).value;
  emit('handleFilter', 'countries', selectedValue);
};

const countries = ref(['Country A', 'Country B']);
const companies = ref(['Company X', 'Company Y']);
const policies = ref(['Policy 1', 'Policy 2']);

const clearFilters = () => {
  localFilterCountries.value = "";
  localFilterCompanies.value = "";
  localFilterPolicy.value = "";
  emit('updateFilter', { filterName: 'countries', value: '' });
  emit('updateFilter', { filterName: 'companies', value: '' });
  emit('updateFilter', { filterName: 'policy', value: '' });
};
</script>

<style scoped>
.filter-bar {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  background-color: #333;
  padding: 20px;
  border-radius: 5px;
}

.filter {
  display: flex;
  flex-direction: column;
}

.filter label {
  color: #FFF;
}

.filter select {
  padding: 8px;
  background-color: #222;
  color: #EEE;
  border: 1px solid #444;
}

.actions button {
  padding: 8px 16px;
  background-color: #555;
  color: #FFF;
  border: none;
  cursor: pointer;
}

.actions button:hover {
  background-color: #666;
}
</style>
