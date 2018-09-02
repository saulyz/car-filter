<template>
    <div class="filter-item boxed dropdown" :class="{open: isDirty}" @click="set">
        More
        <div class="icon">
            <div v-if="isDirty" class="close">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 9.85 9.93" class="x-icon-x "><path style="fill:none;stroke:currentColor;stroke-miterlimit:10" d="M.71.79l8.43 8.43M9.14.71L.71 9.14"></path></svg>
            </div>
            <div v-else class="open">
                <svg class="" viewBox="0 0 8 5" xmlns="http://www.w3.org/2000/svg" stroke-linejoin="round" stroke-linecap="round" stroke-width="1.35"><path d="M7 1.053L4.027 4 1 1" stroke="currentColor" fill="none"></path></svg>
            </div>
        </div>
        <div class="filter-item-options" v-show="isOpen">
            <div v-for="item in items" :key="item.id"
                 class="filter-item-option option-row" 
                 :class="{selected: item.isSelected}"
            >
                <div class="title">
                    <input class="checkbox" type="checkbox" :id="`option-${item.id}`" :checked="item.isSelected"/>
                    <label class="checkbox" for="`option-${item.id}`" @click="onToggle(item.id)">
                        <span>{{item.title}}</span>
                    </label>
                    <span class="only">only</span>
                </div>
                <div class="value">${{item.value}}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        items: {
            type: Array
        },
        onToggle: {
            type: Function
        }
    },
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
            const match = this.items.filter(item => item.isSelected === true);
            return match.length;
        }
    },

    methods: {

        // todo - should get reset event and clear all state

        set() {
            this.isActive = !this.isActive;
        }
    }
}
</script>

<style lang="scss">
    @import "./../assets/config";
    @import "./../assets/checkbox";
    $color-txt-muted: #6d8494;
    $color-option-bg-highlight: #f1f4f7;

    .filter-item.dropdown {
        position: relative;
        display: flex;
        align-items: center;
        
        &.boxed {
            padding-right: 2px;
        }

        &.boxed:hover,
        &.boxed.open {
            cursor: pointer;
            border-color: $color-bg-highlight;
            background-color: $color-bg-highlight;
            color: $color-txt-highlight;
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

    .filter-item-options {
        position: absolute;
        top: 33px;
        right: 0;
        width: 298px;
        padding: 15px 24px 15px;
        font-weight: normal;
        color: $color-txt;
        background: $color-bg;
        border-radius: 2px;
        box-shadow: 0 3px 12px 1px rgba(0,0,0,0.26);
        z-index: 1000;
    }

    .filter-item-option {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .option-row {
        height: 30px;

        .title {
            display: flex;
            align-items: center;
            height: 18px;
            font-size: 14px;
            line-height: 17.5px;
            color: $color-txt;
        }

        .only {
            display: none;
            margin-left: 5px;
            font-size: 12px;
        }

        .value {
            font-size: 12px;
            color: $color-txt-muted;
        }

        &:hover,
        &.selected {

            &:before {
                content: "";
                position: absolute;
                display: block;
                left: 10px;
                width: calc(100% - 20px);
                height: 30px;
                background: $color-option-bg-highlight;
                border-radius: 2px;
                z-index: -1;
            }

            .title,
            .value {
                color: $color-bg-highlight;
            }

            .only {
                display: inline-block;
                padding-top: 2px;
                color: $color-txt-muted;
            }

            .only:hover {
                text-decoration: underline;
            }
        }
    }
</style>
