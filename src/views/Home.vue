<template>
  <div id="home">
    <div class="container">
      <h1>Calculated</h1>
      <div class="wrapper">
        <p>Select your calculator</p>
        <div class="flexbox">
          <div class="item">
            <plus-icon size="1.75x" class="custom-class"></plus-icon>
          </div>
          <div class="item">
            <plus-icon size="1.75x" class="custom-class"></plus-icon>
          </div>
          <div class="item">
            <dollar-sign-icon size="1.75x" class="custom-class"></dollar-sign-icon>
          </div>
          <div class="item">
            <plus-icon size="1.75x" class="custom-class"></plus-icon>
          </div>
          <div class="item">
            <plus-icon size="1.75x" class="custom-class"></plus-icon>
          </div>
          <div class="item">
            <plus-icon size="1.75x" class="custom-class"></plus-icon>
          </div>
          <div class="item">
            <plus-icon size="1.75x" class="custom-class"></plus-icon>
          </div>
          <div class="item">
            <plus-icon size="1.75x" class="custom-class"></plus-icon>
          </div>
        </div>
      </div>
    </div>
    <div class="calculator-container">
      <div class="calculator">
        <h1>{{calcText || "Enter numbers here"}}</h1>
        <div class="buttons">
          <div class="calc-button" @click="buttonClick('ac')">AC</div>
          <div class="calc-button" @click="buttonClick('[+/-]')">[+/-]</div>
          <div class="calc-button">%</div>
          <div class="calc-button" @click="buttonClick('/')">/</div>
          <div class="calc-button" @click="buttonClick('7')">7</div>
          <div class="calc-button" @click="buttonClick('8')">8</div>
          <div class="calc-button" @click="buttonClick('9')">9</div>
          <div class="calc-button" @click="buttonClick('x')">x</div>
          <div class="calc-button" @click="buttonClick('4')">4</div>
          <div class="calc-button" @click="buttonClick('5')">5</div>
          <div class="calc-button" @click="buttonClick('6')">6</div>
          <div class="calc-button" @click="buttonClick('-')">-</div>
          <div class="calc-button" @click="buttonClick('1')">1</div>
          <div class="calc-button" @click="buttonClick('2')">2</div>
          <div class="calc-button" @click="buttonClick('3')">3</div>
          <div class="calc-button" @click="buttonClick('+')">+</div>
          <div class="calc-button long">0</div>
          <div class="calc-button">•</div>
          <div class="calc-button" @click="buttonClick('=')">=</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { DollarSignIcon, PlusIcon } from "vue-feather-icons";
import { constants } from "crypto";

export default {
  data() {
    return {
      calcText: "",
      nums: [],
      operator: ""
    };
  },
  methods: {
    buttonClick: function(number) {
      if (number == "+") {
        if (this.calcText != "") {
          this.nums.push(this.calcText);
          this.calcText = "";
          this.operator = "+";
        }
      } else if (number == "-") {
        if (this.calcText != "") {
          this.nums.push(this.calcText);
          this.calcText = "";
          this.operator = "-";
        }
      } else if (number == "x") {
        if (this.calcText != "") {
          this.nums.push(this.calcText);
          this.calcText = "";
          this.operator = "x";
        }
      } else if (number == "/") {
        if (this.calcText != "") {
          this.nums.push(this.calcText);
          this.calcText = "";
          this.operator = "/";
        }
      } else if (number == "ac") {
        this.calcText = "";
        this.nums = [];
        this.operator = "";
      } else if (number == "=") {
        if (this.calcText != "" && this.nums.length >= 1) {
          this.nums.push(this.calcText);
          this.calcText = "";
          console.log("Do we make it here?");
          switch (this.operator) {
            case "+":
              this.calcText =
                parseFloat(this.nums[0]) + parseFloat(this.nums[1]);
              this.nums = [];
              break;
            case "-":
              this.calcText =
                parseFloat(this.nums[0]) - parseFloat(this.nums[1]);
              this.nums = [];
              break;
            case "x":
              this.calcText =
                parseFloat(this.nums[0]) * parseFloat(this.nums[1]);
              this.nums = [];
              break;
            case "/":
              this.calcText =
                parseFloat(this.nums[0]) / parseFloat(this.nums[1]);
              this.nums = [];
              break;
            default:
              console.log("Present error");
          }
        }
      } else if (number == "[+/-]") {
        if (this.calcText.includes("-")) {
          this.calcText = this.calcText.replace("-", "");
        } else {
          this.calcText = "-" + this.calcText;
        }
      } else {
        this.calcText += number;
      }
    }
  },
  components: {
    PlusIcon,
    DollarSignIcon
  }
};
</script>

<style lang="scss">
#home {
  height: 100vh;
  display: flex;
}

.calculator-container {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #1d293a;

  .calculator {
    width: 360px;

    h1 {
      text-align: right;
    }

    .buttons {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      .calc-button {
        height: 70px;
        width: 70px;
        background: #151e2b;
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 10px 5px;
        color: #eaeaea;
        font-weight: 600;
        font-size: 1.4rem;
        &:hover {
          background: #6c63ff;
        }
      }

      .long {
        width: 170px;
      }
    }
  }
}

.container {
  width: 300px;
  background: #0f1722;
  color: white;
  height: 100%;
  margin: 0;
  padding: 20px;

  .wrapper {
    height: 80%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  h1 {
    margin: 0;
  }

  p {
    margin-bottom: 0;
  }

  .flexbox {
    width: 200px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;

    .item {
      height: 65px;
      width: 65px;
      background: #151e2b;
      margin: 15px;
      display: flex;
      justify-content: center;
      align-items: center;

      &:hover {
        background: #6c63ff;
      }
    }
  }
}
</style>