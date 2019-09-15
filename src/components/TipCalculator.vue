<template>
  <div>
    <div class="calculator">
      <h1 v-if="tip">{{ `$${tip}` }}</h1>
      <h1 v-else>{{"Enter your amout and percent below"}}</h1>
      <input type="number" placeholder="How much is your total?" v-model="total" />
      <input
        type="number"
        placeholder="What percent would you like your tip to be?"
        v-model="percent"
      />
      <div class="btn" @click="buttonClick">Calculate</div>
    </div>
  </div>
</template>

<script>
import {} from "vue-feather-icons";
export default {
  name: "TipCalculator",
  data() {
    return {
      total: null,
      percent: null,
      tip: null
    };
  },
  methods: {
    buttonClick: function() {
      let percentage = this.percent / 100;
      console.log(percentage);
      this.tip = Math.round(percentage * this.total * 100) / 100;
    }
  },
  components: {}
};
</script>

<style lang="scss" scoped>
.calculator {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  h1 {
    text-align: right;
    color: white;
    margin: 5px 0;
  }

  .empty {
    text-align: right;
    margin: 19px 0;
  }

  input {
    height: 68px;
    background: #151e2b;
    color: #eaeaea;
    font-weight: 600;
    font-size: 1.8rem;
    border: none;
    border-bottom: solid 2px #364357;
    text-align: center;
    outline: none;
    text-indent: 15px;
    margin: 5px 0;

    &:hover {
      background: #101720;
      cursor: pointer;
    }

    &::placeholder {
      font-size: 1rem;
    }
  }

  .btn {
    height: 68px;
    width: 200px;
    background: #6c63ff;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #eaeaea;
    font-weight: 600;
    font-size: 1.4rem;
    margin-top: 10px;
    border-bottom: solid 2px #364357;

    &:hover {
      background: #4d47c7;
      cursor: pointer;
    }
  }
}
</style>