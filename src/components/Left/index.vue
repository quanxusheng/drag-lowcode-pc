<template>
    <div class="component-list" @dragstart="handleDragstart">
        <div 
            v-for="(item, index) in list" 
            :key="index"
            :data-index="index"
            class="list"
            draggable
        >
            <span class="iconfont" :class="'icon-' + item.icon"></span>
            <span>{{ item.label }}</span>
        </div>
    </div>
</template>

<script>
import list from '@/custom-component/list'

export default {
    data() { 
        return {
            list,
        }
    },
    mounted() {
    },
    methods: {
        handleDragstart(e) {
            e.dataTransfer.setData('index', e.target.dataset.index)
        },
    },
}
</script>

<style lang="scss" scoped>
.component-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    padding: 10px;

    .list {
        width: 45%;
        border: 1px solid #ddd;
        cursor: grab;
        margin-bottom: 10px;
        text-align: center;
        color: #fff;
        padding: 2px 5px;
        display: flex;
        align-items: center;
        justify-content: center;

        &:active {
            cursor: grabbing;
        }

        .iconfont {
            margin-right: 4px;
            font-size: 20px;
        }

        .icon-wenben,
        .icon-tupian {
            font-size: 18px;
        }
    }
}
</style>