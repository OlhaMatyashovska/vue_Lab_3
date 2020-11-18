<template>
<form v-on:submit.prevent="addNewCompany" class="ClassNewCompany">
            Назва компанії:<br>
            <input v-model="newCompany.Name"><br>
            Число робітників:<br>
            <input type="number" v-model.number="newCompany.NumberOfWorkers"> <br>
            Продукти виробництва:<br>
            <input v-model="newCompany.TypeOfProducts"><br>
            Компанії-співробітники:<br>
            <input v-model="newCompany.Countries"><br>
            <button type="submit">Додати</button>
            <button type="reset">Очистити</button>
</form>
</template>


<script>
export default{
    name:"AddCompanyTemplate",
    props:{
        modelValue:Object
    },
    data(){
        return{
             newCompany:this.modelValue
        }
    },
    methods:{
        addNewCompany(){
            this.$emit("update:modelValue", this.newCompany);
        }
    }
}
</script>


<style>
</style>