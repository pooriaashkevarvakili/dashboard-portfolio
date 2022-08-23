<template>
  <div>
    <v-row>
      <v-col class="col-md-3 col-lg-3 col-sm-12" cols="12">
        <v-card>
          <v-card-title>
            <v-col cols="12" class="text-center" :color="checking ? 'error' : 'info'" @click="takePulse">
              <div>$874</div>
              <div>saleslastmonth</div>
            </v-col>
            <v-spacer></v-spacer>
          </v-card-title>
          <v-sheet color="transparent">
            <v-sparkline :key="String(avg)" :smooth="16" color="accent" :line-width="3" :value="heartbeats" auto-draw
              stroke-linecap="round"></v-sparkline>
          </v-sheet>
        </v-card>
      </v-col>
      <v-col class="col-md-3 col-lg-3 col-sm-12" cols="12">
        <v-card>
          <v-card-title>
            <v-col cols="12" class="text-center" :color="checking ? 'error' : 'info'" @click="takePulse">
              <div>$1283</div>
              <div>salesincome</div>
            </v-col>
            <v-spacer></v-spacer>
          </v-card-title>
          <v-sheet color="transparent">
            <v-sparkline :key="String(avg)" :smooth="16" color="accent" :line-width="3" :value="heartbeats" auto-draw
              stroke-linecap="round"></v-sparkline>
          </v-sheet>
        </v-card>
      </v-col>
      <v-col class="col-md-3 col-lg-3 col-sm-12" cols="12">
        <v-card>
          <v-card-title>
            <v-col cols="12" class="text-center" :color="checking ? 'error' : 'info'" @click="takePulse">
              <div>$1286</div>
              <div>lastmonthsales</div>
            </v-col>
            <v-spacer></v-spacer>
          </v-card-title>
          <v-sheet color="transparent">
            <v-sparkline :key="String(avg)" :smooth="16" color="accent" :line-width="3" :value="heartbeats" auto-draw
              stroke-linecap="round"></v-sparkline>
          </v-sheet>
        </v-card>
      </v-col>
      <v-col class="col-md-3 col-lg-3 col-sm-12" cols="12">
        <v-card>
          <v-card-title>
            <v-col cols="12" class="text-center" :color="checking ? 'error' : 'info'" @click="takePulse">
              <div>$564</div>
              <div>totalrevenue</div>
            </v-col>
            <v-spacer></v-spacer>
          </v-card-title>
          <v-sheet color="transparent">
            <v-sparkline :key="String(avg)" :smooth="16" color="accent" :line-width="3" :value="heartbeats" auto-draw
              stroke-linecap="round"></v-sparkline>
          </v-sheet>
        </v-card>
      </v-col>
    </v-row>

  </div>

</template>
<script>
const exhale = ms => new Promise(resolve => setTimeout(resolve, ms));

export default {
  data: () => ({
    checking: false,
    heartbeats: []
  }),

  computed: {

    avg() {
      const sum = this.heartbeats.reduce((acc, cur) => acc + cur, 0);
      const length = this.heartbeats.length;

      if (!sum && !length) return 0;

      return Math.ceil(sum / length);
    }
  },

  created() {
    this.takePulse(false);
  },

  methods: {
    heartbeat() {
      return Math.ceil(Math.random() * (120 - 80) + 80);
    },
    async takePulse(inhale = true) {
      this.checking = true;

      inhale && (await exhale(1000));

      this.heartbeats = Array.from({ length: 20 }, this.heartbeat);

      this.checking = false;
    }
  }
};
</script>

<style>
</style>
