<template>
  <TableComponent :rows="rows" :columns="columns" resourceType="employee">
    <template v-slot:tb-column="props">
      <span v-if="props.column.label === 'Employee ID'">
          <span>
            {{props.column.label}} <i class="fa fa-bell-o" style="color:blue"></i> 
          </span>
      </span>
      <span v-else>
        {{props.column.label}}
      </span>
    </template>
    <template v-slot:tb-row="props">
      <span v-if="props.column.key === 'id'">
        <code>EMP - {{props.row.id}}</code>
      </span>
    </template>
  </TableComponent>
</template>

<script>
import TableComponent from './components/Tables/Table.vue'

export default {
  name: 'App',
  components: {
    TableComponent
  },
  data () {
    return {
      rows: [
        {
          id: 100,
          name: 'gayathri',
          job: 'VueJs Developer'
        },
        {
          id: 101,
          name: 'Priya',
          job: 'React Developer'
        },
        {
          id: 102,
          name: 'Anu',
          job: 'Angular Developer'
        }
      ],
      columns: [
        {
          key: 'id',
          label: "Employee ID"
        },
        {
          key: 'name',
          label: "Employee Name"
        },
        {
          key: 'job',
          label: "Job Title"
        }
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
