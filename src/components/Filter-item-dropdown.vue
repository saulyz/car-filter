<template>
    <div class="filter-item boxed dropdown" :class="{open: isActive}" @click="set">
        More
        <div class="icon">
            <div v-if="isDirty" class="close">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 9.85 9.93" class="x-icon-x "><path style="fill:none;stroke:currentColor;stroke-miterlimit:10" d="M.71.79l8.43 8.43M9.14.71L.71 9.14"></path></svg>
            </div>
            <div v-else class="open">
                <svg class="" viewBox="0 0 8 5" xmlns="http://www.w3.org/2000/svg" stroke-linejoin="round" stroke-linecap="round" stroke-width="1.35"><path d="M7 1.053L4.027 4 1 1" stroke="currentColor" fill="none"></path></svg>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            isActive: false
        }
    },
    computed: {
        isOpen() {
            return this.isActive;
        },
        isDirty() {
            return false;
        }
    },

    methods: {
        set() {
            this.isActive = !this.isActive;
        }
    }
}
</script>

<style lang="scss">
    .filter-item.dropdown {
        display: flex;
        align-items: center;
        
        &.boxed {
            padding-right: 2px;
        }

        &.boxed:hover,
        &.boxed.open {
            cursor: pointer;
            border-color: #1e93f5;
            background-color: #1e93f5;
            color: #fff;
        }

        .icon {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 20px;
            height: 20px;
            margin-left: 10px;
        }

        .icon .open,
        .icon .close {
            width: 20px;
            padding: 5px;
            transition: transform 0.1s ease;
            transform: rotate(0deg);
        }

        &.boxed.open .icon .open {
            transform: rotate(180deg);
        }
    }
</style>
