<template>
  <v-card>

    <v-col class="col-lg-12 col-md-12 col-sm-12" cols="12">
      <v-btn class="mx-2 mt-5" dark @click="remove">
        remove
      </v-btn>
      <v-row>

        <v-list>
          <v-list-item v-for="(item, index) in items" :key="index">
            <v-checkbox v-model="selected" :value="item" multiple />
            {{ item.title }}
          </v-list-item>
        </v-list>


      </v-row>

    </v-col>
  </v-card>
</template>

<script>
export default {

  data: () => ({
    loading: false,
    selected: [],
    items: [{
      title: 'Wash the car '
    },
    {
      title: 'Task with dropdown menu'
    },
    {
      title: 'wash the car'
    },
    {
      title: 'badge on the risk task'
    }
    ]
  }),
  methods: {
    async load() {


      this.items = items;
      this.loading = false;
    },
    remove() {
      this.items = this.items.filter(i => !this.selected.includes(i));
      this.selected = [];
    }
  }
};
</script>
