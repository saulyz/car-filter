<template>
    <div class="filter-item boxed">
        {{label}}
        <span v-if="price" class="price">
            ${{price}}+
        </span>
    </div>
</template>

<script>
export default {
    props: {
        label: {
            type: String,
            default: ''
        },
        price: {
            type: Number,
            default: null
        }
    }
}
</script>

<style lang="scss">
    .filter-item {
        height: 30px;
        padding: 0 16px;
        font-size: 13px;
        line-height: 28px; 
        font-weight: bold;

        &.boxed {
            color: #51697a;
            border: 1px solid #e0e7ed;
            border-radius: 2px;
        }

        &.boxed:hover {
            cursor: pointer;
            border-color: #1e93f5;
            background-color: #1e93f5;
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
