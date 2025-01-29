<template>
  <v-card title="Test Mostafa Hamdy">
    <template v-slot:text>
      <v-container>
        <v-row>
          <v-col cols="6">
            <v-text-field
              v-model="search"
              label="Search"
              prepend-inner-icon="mdi-magnify"
              variant="outlined"
            ></v-text-field>
          </v-col>

          <v-col cols="3">
            <v-select
              label="Camp"
              :items="[
                'California',
                'Colorado',
                'Florida',
                'Georgia',
                'Texas',
                'Wyoming',
              ]"
              variant="outlined"
              class="mr-1"
            ></v-select>
          </v-col>

          <v-col cols="3">
            <v-select
              label="Tent"
              :items="[
                'California',
                'Colorado',
                'Florida',
                'Georgia',
                'Texas',
                'Wyoming',
              ]"
              variant="outlined"
            ></v-select>
          </v-col>
        </v-row>
      </v-container>
    </template>
    <v-container>
      <v-data-table
        :headers="headers"
        :items="desserts"
        :search="search"
      ></v-data-table>
    </v-container>
  </v-card>
</template>

<script>
import data from "./data.json";

export default {
  data() {
    return {
      search: "",
      headers: [
        { align: "start", key: "hajjId", title: "ID" },
        { key: "name", sortable: false, align: "center", title: "Name" },
        { key: "campNumber", title: "Center (Camp)" },
        { key: "tentNumber", title: "Tent" },
        { key: "bedNumber", title: "Bed" },
      ],
      desserts: data,
    };
  },
};
</script>
<style>
thead {
  background-color: #f6eeb4 !important;
}

:deep(.v-field__outline) {
  border-color: red !important;
}
.v-field__outline {
  border-color: red !important;
}
.v-input__control {
  color: rgb(155, 32, 32) !important;
}
</style>
