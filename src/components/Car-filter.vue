<template>
    <div>
        <div class="filter-label">Car type</div>
        <div class="filter-wrapper">
            <filter-item label="All"></filter-item>
            <filter-item label="pirmas" :price="123"></filter-item>
            <filter-item label="antras" :price="123"></filter-item>
            <filter-item label="trečias" :price="123"></filter-item>
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
