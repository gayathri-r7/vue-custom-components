<template>
  <div>
    <table>
      <thead>
        <tr>
          <th v-for="(column, labelIndex) in columns" :key="labelIndex">
            <slot name="tb-column" :columnIndex="labelIndex" :column="column">
              {{ column.label }}
            </slot> 
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, itemIndex) in rows" :key="itemIndex">
            <td v-for="(column, labelIndex) in columns" :key="labelIndex">
                <slot name="tb-row" :row="item" :rowIndex="itemIndex" :column="column">
                    {{ item[column.key] }}
                </slot> 
            </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>

export default {
  name: 'TableComponent',
  components: {},
  props: ['rows', 'columns', 'resourceType'],
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
table {
  border-collapse: collapse;
  width: 100%;
}
tr:hover {
    background-color: ghostwhite;
    cursor: pointer;
}
table tr {
    border-bottom: 1px solid #f2f2f2;
}
tr:first-child {
  border-top: none;
}
tr:last-child {
  border-bottom: none;
}
th, td {
  text-align: left;
  padding: 8px;
}
th {
  background-color: #f2f2f2;
  color: black;
  text-transform: uppercase;
  /* font-weight: normal; */
  font-family: Arial, Helvetica, sans-serif;
  font-size: 80%;
}
</style>