<template>
    <div>
        <MyTable>
            <template #header>
                <th>#</th>
                <th>商品名称</th>
                <th>价格</th>
                <th>标签</th>
                <th>操作</th>
            </template>
            <template #body="{row,index,list}">
                <td>{{ index + 1 }}</td>
                <td>{{ row.goods_name }}</td>
                <td>{{ row.goods_price }}</td>
                <td>
                    <input
                        v-if="row.inputVisible"
                        class="tag-input form-control"
                        type="text"
                        @blur="row.inputVisible = false"
                        v-focus
                        @keyup.enter="addTag(row, $event)"
                        @keyup.esc="escFn"
                    />
                    <button
                        v-else
                        class="btn btn-primary btn-sm add-tag"
                        @click="row.inputVisible = true"
                    >
                        +Tag
                    </button>
                    <span
                        v-for="item in row.tags"
                        :key="item"
                        class="badge badge-warning"
                        >{{ item }}</span
                    >
                </td>
                <td>
                    <button class="btn btn-danger" @click="del(list, index)">
                        删除
                    </button>
                </td>
            </template>
        </MyTable>
    </div>
</template>

<script>
import MyTable from './MyTable.vue'
export default {
    components: {
        MyTable,
    },
    directives: {
        focus: {
            inserted(el) {
                el.focus()
            },
        },
    },
    methods: {
        addTag(row, e) {
            if (e.target.value.trim() === '') {
                return
            }
            row.tags.push(e.target.value)
            row.inputVisible = false
        },
        del(list, index) {
            // list = list.filter(item => item.id !== id)
            list.splice(index, 1)
        },
        escFn(e) {
            e.target.value = ''
        },
    },
}
</script>

<style></style>
