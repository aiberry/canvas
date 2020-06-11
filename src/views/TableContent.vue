<template>
  <div class="about">
    <h1>This is a table page</h1>
    <Table :tableData="tableData" />
  </div>
</template>

<script>
// @ is an alias to /src
import Table from "@/components/Table.vue";
// eslint-disable-
import axios from "axios";

export default {
  name: "TableContent",
  data() {
    return {
      tableData: [],
    };
  },
  components: {
    Table,
  },
  mounted() {
    axios
      .get("http://fantogramma.org/test.json")
      .then((response) => {
        this.tableData = Object.keys(response.data).map((key) => ({
          key,
          fruit: response.data[key].fruit,
        }));
      })
      .catch(console.log);
  },
};
</script>
