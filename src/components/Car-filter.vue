<template>
    <div>
        <div class="filter-label">Car type</div>
        <div class="filter-wrapper">
            <filter-item label="All"></filter-item>
            <filter-item label="Small" :price="200"></filter-item>
            <filter-item label="Medium" :price="200"></filter-item>
            <filter-item label="Large" :price="200"></filter-item>
            <filter-item label="SUV" :price="190"></filter-item>
            <filter-item label="Van" :price="271"></filter-item>
        </div>
    </div>
</template>

<script>
import FilterItem from './Filter-item.vue';

export default {
    components: {
        FilterItem
    }
}
</script>

<style lang="scss">
    .filter-label {
        padding-bottom: 6px;
        font-size: 10px;
        font-weight: bold;
        text-transform: uppercase;
        text-align: left;
    }

    .filter-wrapper {
        display: flex;
        flex-wrap: wrap;
    }
</style>
