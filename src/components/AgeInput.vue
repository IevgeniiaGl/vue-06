<template>
  <div>
    <h2>Task 01</h2>
    <label>
      Введiть ваш вiк
      <input type="number" v-model="ageValue" :class='checkColor'>
      <br>
      {{info}}
    </label>

  </div>
</template>

<script>
  export default {
    name:"AgeInput",

    props: {

      modelValue: {
        type: Number,
      },

      modelModifiers: {
      default: () => ({}),
    },
    },

    computed: {
     ageValue: {
      get() {
        return this.modelValue
      }, 
      set (newValue){
        if(this.modelModifiers.check && newValue>=150){
        newValue = null
        this.info = 'Вiк не може бути бiльше 150'
        }
        else  this.info = null
        if(this.modelModifiers.setColor && (newValue>0 && newValue<10))
            this.checkColor = "child"
        else if (this.modelModifiers.setColor && (newValue>10 && newValue< 21 )) 
            this.checkColor = "teenager"
        else if (this.modelModifiers.setColor && (newValue>21 && newValue< 150 )) 
            this.checkColor = "adult"
        else 
            this.checkColor = "unCorrect"
        this.$emit('update:modelValue', newValue)
      }
      }
    },

    




  }
</script>

<style lang="scss" scoped>

</style>