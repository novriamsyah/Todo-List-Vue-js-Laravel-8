<template>
<div class="listView">
    <div v-for="(item, index) in items" :key="index" class="item">
        <list-item :item="item" v-on:itemchanged="$emit('reloadList')"/>
    </div>
</div>
</template>

<script>
import listItem from "./listItem";
export default {
    props: ['items'],
    components: {listItem}
}
</script>

<style scoped>
    .listView {
        background:#020631;
        width: 475px;
    }
    .item{
        padding: 5px;
        margin-top: 10px;
        margin-left: -20px;
        background: #ffffff;
        border-radius: 5px;
        margin-bottom: 7px;
        position: relative;
        word-break: break-word;
    }
</style>

