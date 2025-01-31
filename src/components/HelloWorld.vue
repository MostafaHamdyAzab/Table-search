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
              v-model="selectedCamp"
              label="Camp"
              :items="getDistictCamps"
              variant="outlined"
              class="mr-1"
            ></v-select>
          </v-col>

          <v-col cols="3">
            <v-select
              v-model="selectedTent"
              label="Tent"
              :items="getDistictTents"
              variant="outlined"
            ></v-select>
          </v-col>
        </v-row>
      </v-container>
    </template>
    <v-container style="max-height: 400px; overflow-y: auto">
      <v-data-table
        :headers="headers"
        :items="filteredData"
        :search="search"
        height="300px"
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
      selectedCamp: "",
      selectedTent: "",
      headers: [
        { align: "start", key: "hajjId", title: "ID" },
        { key: "name", sortable: false, align: "center", title: "Name" },
        { key: "campNumber", title: "Center (Camp)" },
        { key: "tentNumber", title: "Tent" },
        { key: "bedNumber", title: "Bed" },
      ],
      allData: data,
      filteredData: data,
    };
  },
  computed: {
    getDistictCamps() {
      const uniqueCamps = [
        ...new Set(this.allData.map((item) => item.campNumber)),
      ];

      return uniqueCamps;
    },
    getDistictTents() {
      const uniqueTents = [
        ...new Set(this.allData.map((item) => item.tentNumber)),
      ];

      return uniqueTents;
    },
    // filteredData() {
    //   if (!this.selectedCamp && !this.selectedTent) {
    //     return this.allData;
    //   } else if (this.selectedCamp) {
    //     return this.allData.filter(
    //       (item) => item.campNumber === this.selectedCamp
    //     );
    //   } else if (this.selectedTent) {
    //     return this.allData.filter(
    //       (item) => item.tentNumber === this.selectedTent
    //     );
    //   }
    // },
  },
  watch: {
    selectedCamp(newCamp) {
      if (!newCamp) {
        this.filteredData = this.allData;
      } else {
        // Filter allData when selectedCamp changes
        this.filteredData = this.allData.filter(
          (item) => item.campNumber === newCamp
        );
      }
    },
    selectedTent(newTent) {
      if (!newTent) {
        this.filteredData = this.allData;
      } else {
        // Filter allData when selectedCamp changes
        // this.selectedCamp = "";
        this.filteredData = this.allData.filter(
          (item) => item.tentNumber === newTent
        );
      }
    },
  }, //end watch
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
