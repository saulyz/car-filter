<template>
    <div class="filter-item boxed" :class="{selected: isSelected}" @click="onToggle(id)">
        {{label}}
        <span v-if="price" class="price">
            ${{price}}+
        </span>
    </div>
</template>

<script>
export default {
    props: {
        id: {
            type: Number
        },
        label: {
            type: String,
            default: ''
        },
        price: {
            type: Number,
            default: null
        },
        isSelected: {
            type: Boolean,
            default: false
        },
        onToggle: {
            type: Function
        }
    }
}
</script>

<style lang="scss">
    @import "./../assets/config";

    .filter-item {
        height: 30px;
        margin-bottom: 4px;
        padding: 0 16px;
        font-size: 13px;
        line-height: 28px; 
        font-weight: bold;
        user-select: none;

        &.boxed {
            color: $color-txt;
            border: 1px solid $color-border;
            border-radius: 2px;
        }

        &.boxed:hover,
        &.boxed.selected {
            cursor: pointer;
            border-color: $color-bg-highlight;
            background-color: $color-bg-highlight;
            color: #fff;
        }

        .price {
            margin-left: 10px;
            font-weight: normal;
        }

    }

    .filter-item + .filter-item {
        margin-left: 4px;
    }
</style>
