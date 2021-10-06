<template >
    <div class="list-item">
        <span class="budget-comment">{{item.comment}}</span>
        <span class="budget-value">{{item.value}}</span>
        <el-button type="danger" size="mini" @click="deleteItem(item.id)">Delete</el-button>
    </div>
</template>

<script>
export default {
    name: "BudgetListItem",
    props: {
        item: {
            type: Object,
            default: () => ({})
        }
    },
    methods: {
        deleteItem(id) {
            this.$emit('deleteItem', id)
        }
    }
}
</script>

<style scoped>
.list-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 15px;
}
</style>