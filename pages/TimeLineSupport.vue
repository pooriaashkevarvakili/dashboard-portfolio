<template>
    <v-card>
        <v-card-title>

            <v-layout column align-end>
                <div class="caption grey--text text-uppercase">
                    TimelineSupport
                </div>
                <div class="caption grey--text text-uppercase">
                    34.5 increase
                </div>
            </v-layout>
            <v-spacer></v-spacer>
        </v-card-title>
        <v-timeline align-top dense>
            <v-timeline-item color="teal lighten-3" small>
                <v-row class="pt-1">
                    <v-col cols="3">
                        <strong>3-4pm</strong>
                    </v-col>
                    <v-col>
                        <strong>Design Stand Up</strong>
                        <div class="text-caption mb-2">
                            Hangouts
                        </div>
                        <v-avatar>
                            <v-img
                                src="https://avataaars.io/?avatarStyle=Circle&topType=LongHairFrida&accessoriesType=Kurt&hairColor=Red&facialHairType=BeardLight&facialHairColor=BrownDark&clotheType=GraphicShirt&clotheColor=Gray01&graphicType=Skull&eyeType=Wink&eyebrowType=RaisedExcitedNatural&mouthType=Disbelief&skinColor=Brown">
                            </v-img>
                        </v-avatar>
                        <v-avatar>
                            <v-img
                                src="https://avataaars.io/?avatarStyle=Circle&topType=ShortHairFrizzle&accessoriesType=Prescription02&hairColor=Black&facialHairType=MoustacheMagnum&facialHairColor=BrownDark&clotheType=BlazerSweater&clotheColor=Black&eyeType=Default&eyebrowType=FlatNatural&mouthType=Default&skinColor=Tanned">
                            </v-img>
                        </v-avatar>
                        <v-avatar>
                            <v-img
                                src="https://avataaars.io/?avatarStyle=Circle&topType=LongHairMiaWallace&accessoriesType=Sunglasses&hairColor=BlondeGolden&facialHairType=Blank&clotheType=BlazerSweater&eyeType=Surprised&eyebrowType=RaisedExcited&mouthType=Smile&skinColor=Pale">
                            </v-img>
                        </v-avatar>
                    </v-col>
                </v-row>
            </v-timeline-item>


            <v-timeline-item color="teal lighten-3" small>
                <v-row class="pt-1">
                    <v-col cols="3">
                        <strong>9-11am</strong>
                    </v-col>
                    <v-col>
                        <strong>Finish Home Screen</strong>
                        <div class="text-caption">
                            Web App
                        </div>
                    </v-col>
                </v-row>
            </v-timeline-item>
        </v-timeline>
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
