<template>
  <div class="dynamic-table-container">
       <table>
         <thead>
         <tr>
           <td v-for="country in countries" :key="country">
             {{ country }}
             <table>
               <thead>
               <tr>
                 <td>1212</td>
                 <td>1212121213</td>
               </tr>
               </thead>
             </table>
           </td>
         </tr>
         <tr>

         </tr>
         </thead>
       </table>
  </div>
</template>

<script setup>
import {defineProps, ref} from "vue";

const props = defineProps({
  rowData: Array,
});

const countries = ref([]);

for (const row of props.rowData) {
  countries.value.push(row.country);
}


const toggleExpand = (country) => {
  country.isExpanded = !country.isExpanded;
};

const toggleExpandCompany = (company) => {
  company.isExpanded = !company.isExpanded;
};

</script>

<style scoped>
table {
  width: 100%;
}
   thead {
     background-color: #333;
   }

thead td {
  padding: 10px;
  min-width: 200px;
  border: 1px solid #222;
}
</style>
