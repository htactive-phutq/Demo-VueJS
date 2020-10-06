<template>
  <v-app>
    <v-container>
      <v-card class="mx-auto" max-width="500">
        <v-toolbar color="deep-purple accent-4" dark>
          <v-toolbar-title>List Demo</v-toolbar-title>
          <v-spacer></v-spacer>
        </v-toolbar>

        <v-list subheader>
          <v-subheader>Render List</v-subheader>
          <v-list-item>
            <v-list-item-content>
              <v-text-field label="Value add" v-model="valueAdd"></v-text-field>
            </v-list-item-content>
            <v-list-item-icon>
              <v-btn color="primary" @click="addList">Add</v-btn>
            </v-list-item-icon>
          </v-list-item>
          <v-list-item v-for="item in lists" :key="item.title">
            <v-list-item-avatar>
              <v-img :alt="`${item.title} avatar`" :src="item.avatar"></v-img>
            </v-list-item-avatar>

            <v-list-item-content>
              <v-text-field
                :value="item.title"
                @change="updateValue(item.id, $event)"
              ></v-text-field>
            </v-list-item-content>

            <v-list-item-icon>
              <v-icon color="red" @click="deleteItem(item.id)">
                mdi-delete
              </v-icon>
            </v-list-item-icon>
          </v-list-item>
        </v-list>
      </v-card>
    </v-container>
  </v-app>
</template>
<script>
export default {
  data: () => ({
    valueAdd: "",
    lists: [],
    dataAPI: [
      {
        id: 1,
        active: true,
        avatar: "https://cdn.vuetifyjs.com/images/lists/1.jpg",
        title: "Jason Oner",
      },
      {
        id: 2,
        active: true,
        avatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
        title: "Mike Carlson",
      },
      {
        id: 3,
        avatar: "https://cdn.vuetifyjs.com/images/lists/3.jpg",
        title: "Cindy Baker",
      },
      {
        id: 4,
        avatar: "https://cdn.vuetifyjs.com/images/lists/4.jpg",
        title: "Ali Connors",
      },
    ],
  }),
  methods: {
    getData() {
      //Call API get list
      this.lists = this.dataAPI;
    },
    deleteItem(id) {
      // API thì call API delete rồi gọi hàm get Data
      this.lists = this.lists.filter((item) => item.id !== id);
    },
    updateValue(id, value) {
      this.lists = this.lists.map((item) => {
        if (item.id == id) {
          return { ...item, title: value };
        }
        return item;
      });
    },
    addList() {
      if (this.valueAdd) {
        // call API create
        this.lists = [
          ...this.lists,
          {
            id: Math.ceil(Math.random(1000) * 100),
            avatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
            title: this.valueAdd,
          },
        ];
        this.valueAdd = "";
      }
    },
  },
  mounted() {
    // Load data
    // Call api get list
    this.getData();
    console.log("load Data success");
  },
};
</script>
