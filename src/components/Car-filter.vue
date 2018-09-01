<template>
    <div>
        <div class="filter-label">Car type</div>
        <div class="filter-wrapper">
            <filter-item label="All" :key="0"></filter-item>
            <template v-for="item in filter">
                <filter-item v-if="!item.children" :label="item.title" :price="item.value" :key="item.id"></filter-item>
                <filter-item-dropdown v-else :label="item.title" :children="item.children" :key="item.id"></filter-item-dropdown>
            </template>
        </div>
    </div>
</template>

<script>
import filterData from './../mocks/filter-data.js';
import filterItem from './Filter-item.vue';
import filterItemDropdown from './Filter-item-dropdown.vue';

export default {
    components: {
        filterItem,
        filterItemDropdown
    },
    data() {
        return {
            filter: filterData
        }
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
