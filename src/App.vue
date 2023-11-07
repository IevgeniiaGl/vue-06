
<template>
  <age-input v-model.check.setColor="myAge"/>
  <user-input-url v-model.checkPath="userUrl"/>
  <user-input-email v-model.check="userEmail"/>
   <user-input 
  v-model:age.backgroundAge="userAge" 
  v-model:name.backgroundName="userName"/>
   <card-input 
 v-model:cardNumber="numberValue"
 v-model:cardDate="dateValue"
 v-model:cardCode="codeValue"
 />
</template>

<script>
import AgeInput from './components/AgeInput.vue'
import UserInputUrl from "./components/UserInputUrl.vue"
import UserInputEmail from './components/UserInputEmail.vue'
import UserInput from './components/UserInput.vue'
import CardInput from "./components/CardInput.vue";
  export default {
    name:'App',

    components:{
      AgeInput, UserInputUrl,UserInputEmail, UserInput, CardInput,
    },

    data(){
      return {
        userAge:null,
        userUrl:null,
        userEmail:null,
        userName:null,
        myAge:null,
         numberValue:"",
        dateValue:"MM/YY",
        codeValue:"",
      }
    }
    
  }
</script>


<style lang="scss">
@import "./assets/styles/";


</style>
