<template>
  <div>
    <v-row class="row">
      <v-col class="col-md-4 col-lg-4  col-sm-12" cols="12">
        <HeartRate />
      </v-col>
      <v-col class="col-md-4 col-lg-4  col-sm-12" cols="12">
        <Pc />
      </v-col>
      <v-col class="col-md-4 col-lg-4  col-sm-12" cols="12">
        <Apartemanet />
      </v-col>

    </v-row>
    <v-row>
      <v-col class="col-md-6 col-lg-6  col-sm-12" cols="12">
        <Technical />
      </v-col>
      <v-col class="col-md-6 col-lg-6  col-sm-12" cols="12">
        <TimeLineSupport />
      </v-col>
    </v-row>
    <ChartOne />
    <Table />
    <CheckList />
  </div>
</template>
<script>
import Table from "./Table.vue"
import HeartRate from "./HeartRate.vue"
import Pc from './Pc.vue'
import Apartemanet from './Apartemanet.vue'
import Technical from "./Technical.vue"
import TimeLineSupport from "./TimeLineSupport.vue"
import ChartOne from "./ChartOne.vue"
import CheckList from "./CheckList.vue"
export default {
  layout: 'main',
  components: {
    HeartRate,
    Pc,
    CheckList,
    Apartemanet,
    Technical,
    Table,
    TimeLineSupport,
    ChartOne
  },
};
</script>
<style>
</style>

