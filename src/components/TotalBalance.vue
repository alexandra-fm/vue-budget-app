<template>
    <div class="total-value" v-bind:class="totalClassValue"> Balance: {{ total }} </div>
</template>

<script>
export default {
    name: "TotalBalance",
    props: {
        total: {
            type: Number,
            default: 0
        }
    },
    computed: {
        totalClassValue() {
            return {
                negativeValue:(this.total)<0,
                positiveValue:(this.total)>0,
            }
        }
    }
};
</script>

<style scoped>
.total-value {
    font-size: 26px;
    text-transform: uppercase;
    padding: 20px;
    text-align: center;
}
.positiveValue {
    color:rgb(60, 159, 60)
}
.negativeValue {
    color:rgb(199, 42, 42)
}
</style>