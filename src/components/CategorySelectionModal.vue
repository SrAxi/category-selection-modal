<template>
    <v-app id="inspire">
        <v-row justify="center">
            <v-dialog
                v-model="dialog"
                persistent
                max-width="760"
            >
                <template v-slot:activator="{ on, attrs }">
                    <v-btn
                        color="primary"
                        dark
                        v-bind="attrs"
                        v-on="on"
                    >
                        Open Dialog
                    </v-btn>
                </template>
                <template v-if="isFirstStep">
                    <CategorySelectionView :goNext="goNext" />
                </template>
                <template v-else>
                    <PrizeAndSocialView :close="close" />
                </template>
            </v-dialog>
        </v-row>
    </v-app>
</template>

<script>
    import CategorySelectionView from '@/components/CategorySelectionView'
    import PrizeAndSocialView from '@/components/PrizeAndSocialView'

    export default {
        name: 'CategorySelectionModal',
        components: { CategorySelectionView, PrizeAndSocialView },
        data: () => ({
            dialog: true,
            currentStep: 'first',
        }),
        computed: {
            isFirstStep() {
                return this.currentStep === 'first'
            },
        },
        methods: {
            goNext() {
                this.currentStep = 'second'
            },
            close() {
                this.dialog = false
            },
        },
    }
</script>

<style scoped>

</style>