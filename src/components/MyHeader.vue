<template>
    <div class="my-header" :style="{ backgroundColor: bgc, color }">
        {{ title }}
    </div>
</template>

<script>
export default {
    props: {
        bgc: {
            tyep: String,
            default: '#1d7bff',
        },
        color: {
            type: String,
            default: '#fff',
        },
        title: {
            type: String,
            default: '大标题',
        },
    },
}
</script>

<style lang="less" scoped>
.my-header {
    height: 50px;
    line-height: 50px;
    text-align: center;
    font-size: 16px;
    background-color: red;
    color: #fff;
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
}
</style>
