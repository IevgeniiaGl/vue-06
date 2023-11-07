<template>
  <div>
    <h2>Task 03</h2>
    <label>
      Введiть email
      <input type="text" v-model="emailValue" :class='colorEmail'>
    </label>
  </div>
</template>
<script>
  export default {
    name:"UserInputEmail",
    props: {
      modelValue: {
      type: String,
      },
      modelModifiers: {
      default: () => ({}),
    },
    },
    computed: {
     emailValue: {
      get() {
        return this.modelValue
      }, 
      set (newEmailValue){
        newEmailValue = this.addEdu(newEmailValue)
        this.$emit('update:modelValue', newEmailValue)
      }
      }
    },

    methods: {
      addEdu(newValue) {
        this.checkEdu(newValue)
        if (newValue.match(/@$/g)) {
                newValue =newValue + 'inv.mn.edu'
                this.colorEmail = 'correctValue'
            }
            return newValue
        
      },
      checkEdu(newValue){
        if (newValue.match(/@/g)) {
                if (newValue.match(/@inv\.mn\.edu$/g) !== null) this.colorEMail = 'correctValue'
                else this.colorEmail = 'unCorrectValue'
      }
    },
  }, 
}
</script>

<style lang="scss" scoped>

</style>