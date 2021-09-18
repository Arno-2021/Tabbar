<template>
    <div class="my-tab-bar">
        <div
            class="tab-item"
            :class="{ current: index === active }"
            v-for="(item, index) in bar"
            :key="item.tag"
            @click="switcher(index, item.comName)"
        >
            <span class="iconfont" :class="item.icon"></span>
            <span>{{ item.tag }}</span>
        </div>
        <!-- <div class="tab-item">
            <span class="iconfont icon-sousuo"></span>
            <span>商品搜索</span>
        </div>
        <div class="tab-item">
            <span class="iconfont icon-user"></span>
            <span>用户中心</span>
        </div> -->
    </div>
</template>

<script>
export default {
    props: {
        bar: {
            type: Array,
            required: true,
            validator(value) {
                if (value.length >= 2 && value.length <= 5) {
                    return true
                } else {
                    console.error('只能设置2-5个选项')
                    return false
                }
            },
        },
    },
    data() {
        return {
            active: 0,
        }
    },
    methods: {
        switcher(index, comName) {
            this.active = index
            this.$emit('switcher', comName)
        },
    },
}
</script>

<style lang="less" scoped>
.my-tab-bar {
    position: fixed;
    left: 0;
    bottom: 0;
    width: 100%;
    height: 50px;
    background-color: #fff;
    border-top: 1px solid #ccc;
    display: flex;
    justify-content: space-around;
    align-items: center;
    .tab-item {
        display: flex;
        flex-direction: column;
        align-items: center;
        .iconfont {
            font-size: 18px;
        }
    }
    .current {
        color: #1d7bff;
    }
}
</style>
