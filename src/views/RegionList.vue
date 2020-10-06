<template>
  <v-data-table :headers="headers" :items="desserts" class="elevation-1" hide-default-footer>
    <template v-slot:item.country="{ item }">{{ showCountry(item.country)}}</template>
    <template v-slot:item.action="{ }">
      <v-btn class="mx-2" fab dark small color="cyan">
        <v-icon dark>mdi-pencil</v-icon>
      </v-btn>
    </template>
  </v-data-table>
</template>

<script>
export default {
  name: "RegionList",
  data() {
    return {
      listCountry: [
        { id: 1, name: "Viet Nam" },
        { id: 2, name: "My" },
        { id: 3, name: "Phap" },
        { id: 4, name: "Anh" },
      ],
      headers: [
        {
          text: "Name",
          align: "start",
          sortable: false,
          value: "name",
        },
        { text: "Description", value: "desc", sortable: false },
        { text: "Country", value: "country", sortable: false },
        { text: "Boundary", value: "boundary", sortable: false },
        {
          text: "Centerpoint Longitude",
          value: "c_longitude",
          sortable: false,
        },
        { text: "Centerpoint Latitude", value: "c_latitude", sortable: false },
        { text: "Header Image", value: "header_image", sortable: false },
        { text: "", value: "action", sortable: false },
      ],
      desserts: [
        {
          name: "Frozen Yogurt",
          desc: "đasadasdsadsadasd",
          country: 1,
          boundary: "đâsdsadas",
          c_longitude: "44.312312",
          c_latitude: "-17.3123",
          header_image: "image/abc",
        },
        {
          name: "Frozen Yogurt1",
          desc: "đasadasdsadsadasd",
          country: 2,
          boundary: "đâsdsadas",
          c_longitude: "44.312312",
          c_latitude: "-17.3123",
          header_image: "image/abc",
        },
        {
          name: "Frozen Yogurt2",
          desc: "đasadasdsadsadasd",
          country: 3,
          boundary: "đâsdsadas",
          c_longitude: "44.312312",
          c_latitude: "-17.3123",
          header_image: "image/abc",
        },
        {
          name: "Frozen Yogurt3",
          desc: "đasadasdsadsadasd",
          country: 4,
          boundary: "đâsdsadas",
          c_longitude: "44.312312",
          c_latitude: "-17.3123",
          header_image: "image/abc",
        },
      ],
    };
  },
  methods: {
    showCountry(id) {
      return this.listCountry.find((item) => item.id === id).name;
    },
  },
};
</script>

<style>
</style>
