<template>
    <div>
        <table class="table table-striped table-bordered">
            <thead>
                <tr>
                    <slot name="header"></slot>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(item, index) in list" :key="item.id">
                    <slot
                        name="body"
                        :row="list[index]"
                        :index="index"
                        :list="list"
                    ></slot>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            list: [],
        }
    },
    created() {
        this.getList()
    },
    methods: {
        async getList() {
            const {
                data: { data, status },
            } = await axios.get('https://www.escook.cn/api/goods')
            if (status === 0) {
                console.log(data)
                this.list = data
            }
        },
    },
}
</script>

<style></style>
