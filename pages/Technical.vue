<template>
    <v-card>
        <v-card-title>
            <v-icon :color="checking ? 'error' : 'info'" class="mr-2 " size="64" @click="takePulse">
                mdi-cloud
            </v-icon>
            <v-layout column align-end>
                <div class="caption grey--text text-uppercase">
                    TechnicalSupport
                </div>
                <div class="caption grey--text text-uppercase">
                    34.5 increase
                </div>
            </v-layout>

            <v-spacer></v-spacer>


        </v-card-title>

        <v-sheet color="transparent">
            <v-sparkline :key="String(avg)" :smooth="16" color="accent" :line-width="3" :value="heartbeats" auto-draw
                stroke-linecap="round"></v-sparkline>
        </v-sheet>
    </v-card>
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
