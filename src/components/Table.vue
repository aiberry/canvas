<template>
  <div class="table">
    <h2>Table component</h2>
    <el-table
      :header-cell-class-name="fillHeaderColors"
      :default-sort="{ prop: 'key', order: 'ascending' }"
      :data="tableData"
    >
      <el-table-column
        sortable
        :sort-orders="['ascending', 'descending']"
        prop="key"
        label="Key"
        width="~50%"
        class-name="headerRed[data-v-783f90ce]"
      ></el-table-column>
      <el-table-column
        sortable
        :sort-orders="['ascending', 'descending']"
        prop="fruit"
        label="Fruit"
        width="~50%"
      ></el-table-column>
    </el-table>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Table extends Vue {
  @Prop() private tableData!: object;
  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  fillHeaderColors({ row, column, rowIndex, columnIndex }) {
    if (row[columnIndex].order === "ascending") {
      return "green";
    }
    if (row[columnIndex].order === "descending") {
      return "blue";
    }
  }
}
</script>

<style lang="scss">
el-table {
  width: 100%;
}

th {
  /* stylelint-disable selector-no-qualifying-type */
  &.green {
    background-color: #008000;
  }

  &.blue {
    background-color: #00ff;
  }
}

h2 {
  margin: 40px 0 0;
}

a {
  color: #42b983;
}
</style>
