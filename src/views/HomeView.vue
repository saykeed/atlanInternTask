<template>
  <div class="home">
      <select v-model="query" @change="toggleTable">
        <option value="null">Select a query</option>
        <option value="0">SELECT * FROM Employees; </option>
        <option value="1">SELECT * FROM Employees WHERE id = 1</option>
        <option value="2">SELECT * FROM Employees WHERE country = Nigeria</option>
        <option value="3">SELECT * FROM Employees WHERE role = Frontend</option>
      </select>

      <div class="tables">
        <Table1 v-if="queriedTable == '0'"/>
        <Table2 v-if="queriedTable == '1'"/>
        <Table3 v-if="queriedTable == '2'"/>
        <Table4 v-if="queriedTable == '3'"/>
      </div>
      
  </div>
</template>

<script>
import { ref } from 'vue'
import Table1 from '@/components/Table1.vue'
import Table2 from '@/components/Table2.vue'
import Table3 from '@/components/Table3.vue'
import Table4 from '@/components/Table4.vue'

export default {
  name: 'HomeView',
  components: { Table1, Table2, Table3, Table4 },
  setup() {
    // variables
    const query = ref(null)
    const queriedTable = ref(null)


    // function 
    const toggleTable = () => {
      queriedTable.value = query.value
    }
    return { query, queriedTable, toggleTable }
  }
}
</script>

<style lang="scss" scoped>
    div.home{

      select{
        width: 90%;
        max-width: 400px;
        height: 30px;
        outline: none;
        border: 1px solid blue;
        border-radius: 0.5rem;
        margin: 3rem auto;
      }

      div.tables{
        padding: 0.5rem;
        overflow: auto;
        width: 100%;
      }
    }


</style>