<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="mb-5" cols="12">
        <v-data-table
          :headers="headers"
          :items="info"
          :items-per-page="5"
          class="elevation-1"
        ></v-data-table>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",

  data: () => ({
    headers: [
      {
        text: "categories",
        align: "start",
        sortable: false,
        value: "value",
      },
    ],
    info: [],
  }),
  mounted() {
    axios
      .get("https://api.chucknorris.io/jokes/search?query=all")
      .then((response) => {
        this.info = response.data.result;
        console.log(response.data.result);
      });
  },
};
</script>
