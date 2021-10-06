<template>
    <el-card class="form-card">
        <el-form :model="formData" ref="addItemForm" :rules="rules" >
            <el-form-item label="Type" prop="type">
                <el-select class="type-select" v-model="formData.type" placeholder="Choose type...">
                    <el-option label="Income" value="INCOME"/>
                    <el-option label="Outcome" value="OUTCOME"/>
                </el-select>
            </el-form-item>
            <el-form-item label="Comments" prop="comment">
                <el-input v-model="formData.comment"/>
            </el-form-item>
            <el-form-item label="Value" prop="value">
                <el-input v-model.number="formData.value"/>
            </el-form-item>
            <el-button @click="onSubmit" type="primary">Submit</el-button>
        </el-form>
    </el-card>
</template>

<script>
export default {
    name:"Form",
    data: () => ({
        formData: {
            type: "INCOME",
            comment: "",
            value: 0
        },
        rules: {
        type: [
            { required: true, message: "Please select type", trigger: "blur" }
        ],
        comment: [
            { required: true, message: "Please input comment", trigger: "change" }
        ],
        value: [
            { required: true, message: "Please input value", trigger: "change" },
            { type: "number", message: "Value must be a number", trigger: "change" }
        ]
        }
    }),
    methods: {
        onSubmit() {
            this.$refs.addItemForm.validate(valid => {
                if (valid) {
                    const a = { 
                        ...this.formData,
                         value: this.formData.type === 'INCOME' ? this.formData.value : this.formData.value * -1
                        }
                        console.log(a);
                    this.$emit("submitForm", a);
                    this.$refs.addItemForm.resetFields();
                }                
            });
        }
    }
}
</script>

<style scoped>
.form-card {
    max-width: 500px;
    margin: auto;
}
.type-select {
    width: 100%;
}


</style>