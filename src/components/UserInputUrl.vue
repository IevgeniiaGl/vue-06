<template>
  <div>
    <h2>Task 02</h2>
    <label>
      Введiть url
      <input type="text" v-model="urlValue" :class='colorUrl'>
    </label>
  </div>
</template>
<script>
  export default {
    name:"UserInputUrl",
    props: {
      modelValue: {
      type: String,
      },
      modelModifiers: {
      default: () => ({}),
    },
    },
    computed: {
     urlValue: {
      get() {
        return this.modelValue
      }, 
      set (newValue){
        if(this.modelModifiers.checkPath){
          if(newValue && !newValue.match(/\w{3,}\.js$/))
          this.colorUrl = 'unCorrectValue'
         else this.colorUrl = null
        }
        this.$emit('update:modelValue', newValue)
      }
      }
    },
  }
</script>

<style lang="scss" scoped>

</style>