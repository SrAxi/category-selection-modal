<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png">
        <h3>Category selection modal PoC</h3>
        <h5>By Riccardo Polacci</h5>
        <CategorySelectionModal />
    </div>
</template>

<script>
    import CategorySelectionModal from '@/components/CategorySelectionModal'

    export default {
        name: 'Home',
        components: { CategorySelectionModal },
    }
</script>
