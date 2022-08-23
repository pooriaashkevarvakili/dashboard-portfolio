<template>
  <v-card>
    <v-toolbar flat height="22px">


      <template v-slot:extension>
        <v-tabs v-model="tabs" centered>
          <v-tab>
            SalesReorts
          </v-tab>
          <v-tab>
            Members
          </v-tab>

        </v-tabs>
      </template>
    </v-toolbar>

    <v-tabs-items v-model="tabs">
      <v-tab-item>
        <v-card flat>
          <v-card-text>
            <v-card-title>
              <v-icon :color="checking ? 'error' : 'info'" class="mr-2" size="64" @click="takePulse">
                mdi-account
              </v-icon>
              <v-layout column align-start>
                <div class="caption grey--text text-uppercase">
                  $368 totalleades
                </div>
              </v-layout>
              <v-spacer></v-spacer>
            </v-card-title>
            <v-sheet color="transparent">
              <v-sparkline :key="String(avg)" :smooth="16" color="accent" :line-width="3" :value="heartbeats" auto-draw
                stroke-linecap="round"></v-sparkline>
            </v-sheet>
          </v-card-text>
        </v-card>
      </v-tab-item>
      <v-tab-item>

        <v-card max-width="600" class="mx-auto" flat>


          <v-list subheader two-line>
            <v-subheader inset>LAST MONTH HIGHLIGHTS</v-subheader>

            <v-list-item v-for="folder in folders" :key="folder.title">
              <v-list-item-avatar>
                <v-img max-height="200px" max-width="200px" :src="folder.src" align="right"></v-img>
              </v-list-item-avatar>

              <v-list-item-content>
                <v-list-item-title v-text="folder.title"></v-list-item-title>

                <v-list-item-subtitle v-text="folder.subtitle"></v-list-item-subtitle>
              </v-list-item-content>

              <v-list-item-action>
                <v-list-item-subtitle v-text="folder.titleOne"></v-list-item-subtitle>

              </v-list-item-action>
            </v-list-item>
          </v-list>
        </v-card>

      </v-tab-item>
    </v-tabs-items>
  </v-card>
</template>

<script>
const exhale = ms => new Promise(resolve => setTimeout(resolve, ms));
import { mapState } from 'vuex'
export default {

  data() {
    return {

      folders: [
        {
          subtitle: 'Web Developer',
          title: 'Ella-Rose Henry',
          src: '1.jpg',
          titleOne: '$564'
        },
        {
          titleOne: '$564',
          src: '5.jpg',
          subtitle: 'UI Designer',
          title: 'Ruben Tillman',
        },
        {
          titleOne: '$564',
          src: '8.jpg',
          subtitle: 'Java Programmer',
          title: 'Vinnie Wagstaff',
        },
      ],
      checking: false,
      heartbeats: [],
      tabs: null,
      text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
    }
  },
  computed: {
    ...mapState({
      tab: state => state.tab
    }),
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
}
</script>
<style>
</style>
