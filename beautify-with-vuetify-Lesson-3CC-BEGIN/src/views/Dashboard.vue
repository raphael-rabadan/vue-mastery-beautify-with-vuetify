<template>
  <div>
    <h1>Dashboard</h1>
    <v-data-table
      :headers="headers"
      :items="employees"
      :items-per-page="5"
      class="elevation-1"
      :sort-by="['name', 'title', 'salary']"
      :sort-desc="[false, false, false]"
      multi-sort
      @click:row="selectRow"
    ></v-data-table>
    <v-snackbar v-model="snackbar">
      You have selected {{ currentItem.name }} and the title is
      {{ currentItem.title }}
      <v-btn color="pink" text @click="snackbar = false">
        Close
      </v-btn>
    </v-snackbar>
  </div>
</template>

<script>
/* eslint-disable */
import employeesJson from "../data/employees.json";

export default {
  name: "DashboardPage",
  data() {
    return {
      currentItem: "",
      snackbar: false,
      headers: [
        {
          text: "ID",
          align: "start",
          sortable: false,
          value: "id",
        },
        { text: "Name", value: "name" },
        { text: "Title", value: "title" },
        { text: "Salary", value: "salary" },
      ],
      employees: employeesJson,
    };
  },
  methods: {
    selectRow(event) {
      this.snackbar = true;
      this.currentItem = event;
    },
  },
};
</script>

<style></style>
