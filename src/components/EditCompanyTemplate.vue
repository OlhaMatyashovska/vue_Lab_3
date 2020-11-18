<template>
<form v-on:submit.prevent="EditCompany" class="ClassNewCompany" v-if="showEditForm1">
<button v-on:click="hide"> X </button>
            Назва компанії:<br>
            <input v-model="editCompany.Name"><br>
            Число робітників:<br>
            <input type="number" v-model.number="editCompany.NumberOfWorkers"> <br>
            Продукти виробництва:<br>
            <input v-model="editCompany.TypeOfProducts"><br>
            Компанії-співробітники:<br>
            <input v-model="editCompany.Countries"><br>
            <button type="submit">Редагувати</button>
            <button type="reset">Очистити</button>
           </form>
</template>


<script>
export default
{
    name:"EditCompanyTemplate",
    data(){
        return{
           showEditForm1:false,
           editCompany:this.modelValue
        }
    },
    props:{
       modelValue:Object
    },
     methods:{
        EditCompany(){
            this.$emit("update:modelValue", this.editCompany);
            this.hide();
        },
        show(){
             this.showEditForm1=true;
        },
        hide(){
             this.showEditForm1=false;
        }
    },
    watch:{
      modelValue(newValue){
        this.editCompany = newValue;
      }
    }
}

</script>
<style>
</style>