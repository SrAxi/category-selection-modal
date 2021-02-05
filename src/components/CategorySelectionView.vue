<template>
    <v-card>
        <v-card-title class="headline justify-center">
            What do you like doing the most?
        </v-card-title>
        <v-card-title class="justify-center grey--text mt-0 pt-0">Select your favourite categories!</v-card-title>
        <v-card-text>
            <v-container fluid>
                <v-row dense>
                    <v-col
                        v-for="card in cards"
                        :key="card.id"
                        :cols="card.flex"
                    >
                        <v-card
                            class="category"
                            @click="selectCategory(card.id)"
                            :class="[isActive(card.id) ? 'active' : '']"
                        >
                            <v-img
                                :src="card.src"
                                class="white--text align-end"
                                gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                                height="200px"
                            >
                                <v-card-title class="justify-center" style="word-break: break-word"
                                              v-text="card.title"></v-card-title>
                            </v-img>
                        </v-card>
                    </v-col>
                    <small class="ml-1">Min. 3, Max. 5</small>
                </v-row>
            </v-container>
        </v-card-text>
        <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
                :color="grouponColor"
                class="white--text"
                @click="goNext"
                :disabled="!canContinue"
            >
                Continue
            </v-btn>
        </v-card-actions>
    </v-card>
</template>

<script>
    export default {
        name: 'CategorySelectionView',
        props: {
            goNext: {
                type: Function,
            }
        },
        data: () => ({
            cards: [
                {
                    id: 1,
                    title: 'Things to Do Leisure',
                    src: 'https://img.grouponcdn.com/deal/g2TEd2BCjLZcESEePbbx/81-700x420/v1/c349x211q85.jpg',
                    flex: 4
                },
                {
                    id: 2,
                    title: 'Things to Do Live',
                    src: 'https://img.grouponcdn.com/deal/tWNnTNXtwDVn5gJCmpfH/uX-2048x1229.jpg/v1/c349x211q85.jpg',
                    flex: 4
                },
                {
                    id: 3,
                    title: 'Health Beauty Wellness',
                    src: 'https://img.grouponcdn.com/deal/3jNspr8THLkfiXuBET2GVu9KikQw/3j-1407x844/v1/c349x211q85.jpg',
                    flex: 4
                },
                {
                    id: 4,
                    title: 'Hotel',
                    src: 'https://img.grouponcdn.com/deal/74HUxdZGKYWc6jhJwBfr/J3-3644x2186/v1/c414x250q85.jpg',
                    flex: 4
                },
                { id: 5, title: 'Tours', src: 'https://cdn.vuetifyjs.com/images/cards/plane.jpg', flex: 4 },
                {
                    id: 6,
                    title: 'Food & Drink',
                    src: 'https://img.grouponcdn.com/deal/45euL5X886iVdYjQ1mzMgqzHvLBN/45-2048x1229/v1/c349x211q85.jpg',
                    flex: 4
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