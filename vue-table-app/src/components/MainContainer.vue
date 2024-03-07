<template>
  <div class="mainContainer">
    <FilterBar
        :filterCountries="filterCountries"
        :filterCompanies="filterCompanies"
        :filterPolicy="filterPolicy"
        @handleClearFilter="handleClearFilter"
        @handleFilter="handleFilter"/>
    <DynamicTable :rowData="filteredData"/>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, computed } from 'vue';
import FilterBar from './FilterBar.vue';
import DynamicTable from './DynamicTable.vue';

export default defineComponent({
  name: 'MainContainer',
  components: {
    FilterBar,
    DynamicTable,
  },
  setup() {
    const rowData = ref([
      { id: 1, country: 'Finland', company: 'Company A', policy: 'Policy X', amount: 1000 },
      { id: 2, country: 'Sweden', company: 'Company B', policy: 'Policy Y', amount: 2000 },
    ]);

    const filterCountries = ref("");
    const filterCompanies = ref("");
    const filterPolicy = ref("");

    const handleClearFilter = () => {
      filterCountries.value = "";
      filterCompanies.value = "";
      filterPolicy.value = "";
    };

    const handleFilter = (filters: { filterName: string, value: string }) => {
      if (filters.filterName === 'countries') filterCountries.value = filters.value;
      else if (filters.filterName === 'companies') filterCompanies.value = filters.value;
      else if (filters.filterName === 'policy') filterPolicy.value = filters.value;
    };

    const filteredData = computed(() => {
      return rowData.value.filter(item =>
          (filterCountries.value === "" || item.country === filterCountries.value) &&
          (filterCompanies.value === "" || item.company === filterCompanies.value) &&
          (filterPolicy.value === "" || item.policy === filterPolicy.value)
      );
    });

    return {
      filterCountries,
      filterCompanies,
      filterPolicy,
      handleClearFilter,
      handleFilter,
      filteredData,
    };
  },
});
</script>

<style scoped>
.mainContainer {
  /* Your styles here */
}
</style>
