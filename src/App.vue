<template>
    <div class="app">
        <MyHeader title="tabbar案例"></MyHeader>
        <keep-alive>
            <component :is="comName"></component>
        </keep-alive>
        <MyFooter :bar="bar" @switcher="switcher"></MyFooter>
    </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyFooter from './components/MyFooter.vue'
import MyGoodsList from './components/MyGoodsList.vue'
import MySearch from './components/MySearch.vue'
import MyUser from './components/MyUser.vue'
export default {
    components: {
        MyHeader,
        MyFooter,
        MyGoodsList,
        MySearch,
        MyUser,
    },
    data() {
        return {
            bar: [
                {
                    icon: 'icon-shangpinliebiao',
                    tag: '商品列表',
                    comName: 'MyGoodsList',
                },
                { icon: 'icon-sousuo', tag: '商品搜索', comName: 'MySearch' },
                { icon: 'icon-user', tag: '用户中心', comName: 'MyUser' },
            ],
            comName: 'MyGoodsList',
        }
    },
    methods: {
        switcher(comName) {
            this.comName = comName
        },
    },
}
</script>

<style lang="less" scoped>
.app {
    padding: 50px 0;
}
</style>
