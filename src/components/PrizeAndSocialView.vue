<template>
    <v-card>
        <v-card-title class="headline justify-center">
            Congratulations!!! 🎉🎉🎉
        </v-card-title>
        <v-card-title class="justify-center grey--text mt-0 pt-0">You won an awesome prize!
        </v-card-title>
        <v-card-text>
            <v-img
                :src="'http://img.grouponcdn.com/gpn/2DGGrsXnrgwLk5jzTQ3B/UM-720x300'"
                class="white--text align-end"
                gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                height="300px"
            />
        </v-card-text>
        <v-divider />
        <v-card-title class="headline justify-center">
            Do you want to win another prize?
        </v-card-title>
        <v-card-title class="justify-center grey--text mt-0 pt-0">Simply share your favourite categories with your friends!</v-card-title>
        <v-card-text>
            <v-container fluid>
                <v-row dense justify="center">
                    <v-col
                        v-for="social in socials"
                        :key="social.id"
                        :cols="social.flex"
                    >
                        <v-btn
                            icon
                            tile
                            href="#"
                            :title="social.title"
                        >
                            <v-icon
                                x-large
                                :color="social.color"
                            >{{ social.icon }}
                            </v-icon>
                        </v-btn>
                    </v-col>
                </v-row>
            </v-container>
        </v-card-text>
        <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
                :color="grouponColor"
                class="white--text"
                @click="close"
            >
                Close
            </v-btn>
        </v-card-actions>
    </v-card>
</template>

<script>
    export default {
        name: 'PrizeAndSocialView',
        props: {
            close: {
                type: Function,
            }
        },
        data: () => ({
            socials: [
                {
                    id: 1,
                    icon: 'mdi-facebook',
                    color: 'blue darken-2',
                    title: 'Share on Facebook',
                    flex: 2,
                },
                {
                    id: 2,
                    icon: 'mdi-instagram',
                    color: 'red lighten-1',
                    title: 'Share on Instagram',
                    flex: 2,
                },
                {
                    id: 3,
                    icon: 'mdi-twitter',
                    color: 'blue lighten-1',
                    title: 'Share on Twitter',
                    flex: 2,
                },
                {
                    id: 4,
                    icon: 'mdi-pinterest',
                    color: 'red lighten-1',
                    title: 'Share on Pinterest',
                    flex: 2,
                },
                {
                    id: 5,
                    icon: 'mdi-snapchat',
                    color: 'black',
                    title: 'Share on Snapchat',
                    flex: 2,
                },
            ],
            grouponColor: '#53a318',
            selectedCategories: [],
        }),
        computed: {
            canContinue() {
                return this.selectedCategories.length >= 3
            },
        },
        methods: {
            selectCategory(cardId) {
                if (!this.selectedCategories.includes(cardId)) {
                    if (this.selectedCategories.length < 5) {
                        this.selectedCategories.push(cardId)
                    }
                } else {
                    this.selectedCategories = [...this.selectedCategories.filter(id => id !== cardId)]
                }
            },
            isActive(cardId) {
                return this.selectedCategories.includes(cardId)
            },
        },
    }
</script>

<style scoped>
    .category:hover {
        cursor: pointer;
        box-sizing: border-box;
    }

    .active {
        box-shadow: 0 0 0 .3rem #53a318 !important;
    }
</style>