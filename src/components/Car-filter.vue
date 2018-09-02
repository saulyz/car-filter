<template>
    <div>
        <div class="filter-label">Car type</div>

        <div class="filter-wrapper">
            <filter-item label="All" :key="0" :on-toggle="reset" :is-selected="isReset"></filter-item>
            <filter-item v-for="item in filterItemsPlain"
                        :id="item.id"
                        :label="item.title" 
                        :price="item.value" 
                        :is-selected="item.isSelected"
                        :on-toggle="toggleItem"
                        :key="item.id">
            </filter-item>
            <filter-item-dropdown label="More" 
                                  :items="filterItemsDropdown">
            </filter-item-dropdown>
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
            filter: filterData,
            filterItemsPlain: [],
            filterItemsDropdown: []
        }
    },
    computed: {
        isReset() {
            let selected = this.filter.filter(item => item.isSelected === true);
            return (selected.length === 0);
        }
    },

    created() {
        // filter can be also set via API _here_

        this.filter.map(item => {
            if (item.type === 'grouped') {
                this.filterItemsDropdown.push(item);
            } else {
                this.filterItemsPlain.push(item);
            }
        })
    },

    methods: {
        reset() {
            this.filter.map(item => {
                item.isSelected = false;
            })
        },

        toggleVal(item) {
            item.isSelected = !item.isSelected;
        },
        
        toggleItem(id, only=false) {
            console.log(id, 'is now selected. With flag only =', only);

            if (only) {
                this.reset();
            }
            let match = this.filter.filter(item => item.id === id);
            this.toggleVal(match[0]);
        }
    }
}
</script>

<style lang="scss">
    @import "./../assets/config";
    
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
