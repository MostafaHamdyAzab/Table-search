<template>
  <v-card title="Nutrition" flat>
    <template v-slot:text>
      <v-text-field
        v-model="search"
        label="Search"
        prepend-inner-icon="mdi-magnify"
        variant="outlined"
        hide-details
        single-line
      ></v-text-field>
    </template>

    <v-data-table
      :headers="headers"
      :items="desserts"
      :search="search"
    ></v-data-table>
  </v-card>
</template>

<script>
import data from "./data.json";
export default {
  data() {
    return {
      search: "",
      headers: [
        {
          align: "start",
          key: "hajjId",

          title: "hajjId",
        },
        { key: "name", sortable: false, align: "center", title: "name" },
        { key: "campId", title: "campId" },
        { key: "passportNumber", title: "passportNumber" },
      ],
      desserts: data,
    };
  },
};
</script>
