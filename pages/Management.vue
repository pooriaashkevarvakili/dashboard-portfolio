<template>
  <div>
    <v-row>
      <v-col class="col-md-4 col-lg-4 col-sm-12" cols="12">
        <v-container>
          <v-row dense>
            <v-col v-for="(item, i) in items" :key="i" cols="12">
              <v-card :color="item.color" dark>
                <div class="d-flex  justify-space-between">
                  <div>
                    <v-card-title class="headline" v-text="item.title"></v-card-title>
                    <v-card-subtitle v-text="item.artist"></v-card-subtitle>
                  </div>
                  <v-card-title class="headline" v-text="item.toman"></v-card-title>

                </div>
              </v-card>
            </v-col>

          </v-row>

        </v-container>
      </v-col>
      <v-col class="col-md-4 col-lg-4 col-sm-12" cols="12">
        <v-container>
          <v-row dense>
            <v-col v-for="(item, i) in itemsOne" :key="i" cols="12">
              <v-card :color="item.color" dark>
                <div class="d-flex  justify-space-between">
                  <div>
                    <v-card-title class="headline" v-text="item.title"></v-card-title>
                    <v-card-subtitle v-text="item.artist"></v-card-subtitle>
                  </div>
                  <v-card-title class="headline" v-text="item.toman"></v-card-title>

                </div>
              </v-card>
            </v-col>

          </v-row>

        </v-container>
      </v-col>
      <v-col class="col-md-4 col-lg-4 col-sm-12" cols="12">
        <v-container>
          <v-row dense>
            <v-col v-for="(item, i) in itemsTwo" :key="i" cols="12">
              <v-card :color="item.color" dark>
                <div class="d-flex  justify-space-between">
                  <div>
                    <v-card-title class="headline" v-text="item.title"></v-card-title>
                    <v-card-subtitle v-text="item.artist"></v-card-subtitle>
                  </div>
                  <v-card-title class="headline" v-text="item.toman"></v-card-title>

                </div>
              </v-card>
            </v-col>

          </v-row>

        </v-container>
      </v-col>
    </v-row>
    <v-row>
      <v-col class="col-md-4 col-lg-4 col-sm-12" cols="12">
        <ChartFront />


      </v-col>
      <ChartTwo />

    </v-row>





  </div>

</template>

<script>
import ChartTwo from "./chartTwo.vue"
import ChartFront from './ChartFront.vue'
export default {
  layout: 'main',
  components: { ChartFront, ChartTwo },

  data: () => ({
    items: [
      {
        color: '#e6b5e4',

        title: 'totalOrders',
        artist: 'lastYeareXprince',
        toman: '$1896'
      },

    ],
    itemsOne: [
      {
        color: '#1ed3e6',

        title: 'clients',
        artist: 'totalClinetsprofit',
        toman: '$598'
      },
    ],
    itemsTwo: [
      {
        color: '#89c645',

        title: 'followers',
        artist: 'peopleinstrted',
        toman: '46%'
      },
    ]
  }),
}
</script>

<style>
</style>
