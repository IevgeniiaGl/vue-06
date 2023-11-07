
<template>
 <h2>Task 06</h2>
  <div class=card>
    <label><span>Card Number</span>
      <input type="text" v-model="currentNumberValue" class="number-input" />
    </label>
  <br>
<div class="card-info">
    <label><span>Expire date</span>
      <input type="text" v-model="currentDateValue" class="date-input">
    </label>
    <label><span>Secure code</span>
      <input type="text" v-model="currentCodeValue" class="code-input">
    </label>
    </div> 
  </div>
</template>

<script>

export default {
  name: 'CardInput',

  props: {
   cardNumber: {
    type: String,
    },
      cardDate: {
    type: String,
    },
       cardCode: {
    type: String,
    },
  
  },

  computed: {
    //=============================================
    currentNumberValue: {
      get() {
        return this.cardNumber;
      },
      set(value) {
        value = this.truncate(value,19)
        value = value.replace(/\s/g, "");
        value = value.replace(/(\d{4}(?=.+))/g, "$1 ");
        this.$emit("update:cardNumber", value);
      },
    },

    currentDateValue:{
      get() {
        return this.cardDate;
      },
      set(value) {
        value = this.truncate(value,5)
        value = value.replace(/(\d{2})(\d{2})/, "$1/$2");
        this.$emit("update:cardDate", value);
      },
  },

      currentCodeValue:{
      get() {
        return this.cardCode;
      },
      set(value) {
        value = this.truncate(value,3)
        this.$emit("update:cardCode", value);
      },
  },



  },
  methods: {
    truncate(value, maxlength) {
    return (value.length > maxlength) ?
    value.slice(0, maxlength - 1) + '' : value;
}
  },
}
</script>








<style lang="scss" scoped>

input{
  border-radius: 4px;
  padding: 5px;
    margin-bottom: 15px;
}
.card{
  width: 320px;
  background: #eae9e9;
  padding: 25px 50px;
}
.card-info{
  display: flex;
  gap: 15px;
}
.number-input{
  width: 100%;
  background: rgb(255, 208, 120) url('../assets/img/visa.png') right  no-repeat;
}
.code-input{
  background:  #ffffff url('../assets/img/question.png') right /16px no-repeat;
}
</style>
