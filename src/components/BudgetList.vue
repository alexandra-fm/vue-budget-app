<template>
    <div class="budget-list-wrap">
        <el-card :header="header">
            <template v-if="!isEmpty">
                <BudgetListItem v-for="(item, prop) in list" :item="item" :key="prop" @deleteItem='onDeleteItem'/>
                <!-- <div class="list-item" v-for="(item, prop) in list" :key="prop">
                    <span class="budget-comment">{{item.comment}}</span>
                    <span class="budget-value">{{item.value}}</span>
                    <el-button type="danger" size="mini" @click="deleteItem(item.id)">Delete</el-button>
                    <BudgetListItem :item="item" @deleteItem='onDeleteItem'/>
                </div> -->
            </template>
            <el-alert v-else type="info" :title="emptyTitle" :closable="false"></el-alert>
        </el-card> 
    </div>
</template>

<script>

import BudgetListItem from './BudgetListItem.vue';

export default {
    name: "BudgetList",
    components: {
        BudgetListItem
    },
    props: {
        list: {
            type: Object,
            default: () => ({})
        }
    },
    data: () => ({
        header: "Budget List",
        emptyTitle: "Empty List",
    
    }),
    computed: {
        isEmpty() {
            return !Object.keys(this.list).length;
        }
    },
    methods: {
        onDeleteItem(id) {
            this.$delete(this.list, id)
        },
        /* deleteItem(id) {
            this.$emit('deleteItem', id)
        } */
    }
}
</script>

<style scoped>
.budget-list-wrap {
    max-width: 500px;
    margin: auto;
}

/* .list-item {
    display: flex;
    align-items: center;
    padding: 10px 15px;
} */

.budget-value {
    font-weight: bold;
    margin-left: auto;
    margin-right: 20px;
}
</style>