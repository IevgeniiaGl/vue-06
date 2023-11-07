<template>
  <div>
    <h2>Task 04</h2>
    <label>Введiть ваше ім’я
      <input type="text" v-model="nameValue" :class='colorName'>
      </label>
  <br>
    <label>Введiть ваш вiк
      <input type="number" v-model="ageValue" :class='colorAge'>
      </label>
  </div>

</template>

<script>
  export default {
    name:"UserInput",

    props: {
      age: {type: Number},
      name: {type:String},
      ageModifiers: {default: () => ({})},
      nameModifiers: {default: () => ({})},
    },

    data(){
    return {
      colorName:'noValue',
      colorAge:'',
    }
  },

    computed: {
      //- - - - -- - - - - -- -- -- - -- -- -- -- - -- -- - -- -  
      nameValue: {
      get() {
        return this.name
      }, 
      set (newValue){
        if (this.nameModifiers.backgroundName){
          if(newValue) this.colorName = null
          else this.colorName ='noValue'
        }
        this.$emit('update:name', newValue)
    
      }  },

      //- - - - -- - - - - -- -- -- - -- -- -- -- - -- -- - -- - 

     ageValue: {
      get() {
        return this.age
      }, 
      set (newValue){
        if(this.ageModifiers.backgroundAge && newValue){
          if (newValue<18)this.colorAge = "unCorrectValue"
          else this.colorAge = "correctValue"
        }
        this.$emit('update:age', newValue)
      }
    }
  }
}
     

     
</script>

<style lang="scss" scoped>
input{
  margin-bottom: 15px;
}

</style>