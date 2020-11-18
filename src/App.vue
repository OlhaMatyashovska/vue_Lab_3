<template>
     <div>
          <h1>Lab_9</h1>
          <p>Variant 4</p>
          Вибрано компaнію {{selected}}
          <input type="button" value="Редагувати інформацію про компанію" v-on:click="showEditForm">
          <input type="button" value="Вилучити" v-on:click="deleteCompany"><br>
          <input type="number" placeholder="min" v-model.number="minWorkerCount">
          <input type="number" placeholder="max" v-model.number="maxWorkerCount">
          <input type="button" value="знайти" v-on:click="Find()">
          <add-company-template v-model="newCompany" @submit.prevent="addNewCompany"></add-company-template>
           <edit-company-template v-model="editCompany" @submit.prevent="EditCompany" ref="editCompanyTemplate"></edit-company-template>
           <br>
        <ul class="companyList">
           <company-template v-for="c in companies" :key="c.Id" class="companyvue" v-on:click="selectCompany(c.Id)" v-bind:company="c">
            </company-template>
          </ul>
      </div>
</template>
<script>
import CompanyTemplate from "./components/CompanyTemplate.vue";
import EditCompanyTemplate from "./components/EditCompanyTemplate.vue";
import AddCompanyTemplate from "./components/AddCompanyTemplate.vue";
export default{
  name:"App",
  components:{
    CompanyTemplate,
    EditCompanyTemplate,
    AddCompanyTemplate
  },
  data(){
    return{
      selected:-1,
      minWorkerCount:0,
      maxWorkerCount:0,
      companies:
      [
        {
          Id:1346,
          Name:"Neuralink",
          Countries:["USA","Canada","Germany"],
          NumberOfWorkers:100,
          TypeOfProducts:"biological engineering"
        },
        {
          Id:1346456,
          Name:"Tesla",
          Countries:["USA","Germany","China"],
          NumberOfWorkers:1000,
          TypeOfProducts:"car production, battery construction"
       },
        {
          Id:13461098,
          Name:"Google",
          Countries:["USA","Great Britain"],
          NumberOfWorkers:100000,
          TypeOfProducts:"search engine studies, hardware and software production"
        }
      ],
      newCompany:
      {
          Name:"",
          Countries:"",
          NumberOfWorkers:0,
          TypeOfProducts:""
      },
      editCompany: {},

    };
  },
    methods:
    {
      addNewCompany()
      {
      let newCompanyCopy = Object.assign({}, this.newCompany);
      newCompanyCopy.Countries=newCompanyCopy.Countries.split(",");
      newCompanyCopy.Id=parseInt(Date.now());
      this.companies.push(newCompanyCopy);
      },
      selectCompany(id){
        this.selected=id;
      },
        showEditForm(){
          let index=this.companies.findIndex(company => company.Id == this.selected);
      if (this.selected>=0)
      {
        this.editCompany = this.companies[index];
        console.log(this.editBook);
        this.$refs.editCompanyTemplate.show();
      }
      else alert("Виберіть");
    },
    EditCompany(){
     this.$refs.editCompanyTemplate.show();
    }, 
    deleteCompany(){
      let index=this.companies.findIndex(company => company.Id == this.selected);
      this.companies.splice(index,1);
    },
    Find(){
        var z=this.minWorkerCount;
        var m=this.maxWorkerCount;
         this.companies=this.companies.filter(x=>Number(x.NumberOfWorkers)>=z && Number(x.NumberOfWorkers)<=m);
    }
  },
};
</script>
<style>
body{
  background:black;
  background-image: url("https://get.agorize.com/wp-content/uploads/2018/01/IMAGE-COUVERTURE-ARTICLE-1.gif");
  color:black;
  position:relative;
}
.companyList{
  list-style-type:none; 
  position:absolute;
  top:400px;
  left:350px;
}
.companyvue
{
  float:left;
  width:200px;
  height:250px;
  background:grey;
  margin:10px;
  color:white;
  
}
form
{
  background:grey;
  width:200px;
  height:250px;
  color:white;
  margin:10px;
}
</style>
