<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png">
        <CategorySelectionModal />
    </div>
</template>

<script>
    // @ is an alias to /src
    // import HelloWorld from '@/components/HelloWorld.vue'

    import CategorySelectionModal from '@/components/CategorySelectionModal'

    export default {
        name: 'Home',
        components: { CategorySelectionModal },
        // components: {
        //   HelloWorld
        // }
    }
</script>
