<template>
    <li>
          
                <h2>{{company.Name}}</h2>
                <p>Виробництво:{{company.TypeOfProducts}}</p>
                <p>Кількість робітників:{{company.NumberOfWorkers}}</p>
               Країни-співробітники:
                 <ul>
                  <li v-for="country in company.Countries" :key="country">{{country}}</li>
                </ul>
    </li>
</template>


<script>
export default{
    name:"CompanyTemplate",
    props:{
        company:Object
    }
}
</script>


<style>
</style>