<template>
  <div>
    <div class="calculator">
      <h1 v-if="calcText">{{calcText.toLocaleString()}}</h1>
      <h3 class="empty" v-else-if="operator">{{ `${nums[0].toLocaleString()} ${operator}`}}</h3>
      <h3 class="empty" v-else-if="!calcText && nums.length == 0">Enter numbers</h3>
      <div class="buttons">
        <div class="calc-button" @click="buttonClick('ac')">AC</div>
        <div class="calc-button" @click="buttonClick('[+/-]')">[+/-]</div>
        <div class="calc-button" @click="buttonClick('%')">%</div>
        <div class="calc-button" @click="buttonClick('/')">÷</div>
        <div class="calc-button" @click="buttonClick('7')">7</div>
        <div class="calc-button" @click="buttonClick('8')">8</div>
        <div class="calc-button" @click="buttonClick('9')">9</div>
        <div class="calc-button" @click="buttonClick('x')">
          <x-icon size="1.1x" class="custom-class"></x-icon>
        </div>
        <div class="calc-button" @click="buttonClick('4')">4</div>
        <div class="calc-button" @click="buttonClick('5')">5</div>
        <div class="calc-button" @click="buttonClick('6')">6</div>
        <div class="calc-button" @click="buttonClick('-')">
          <minus-icon size="1.1x" class="custom-class"></minus-icon>
        </div>
        <div class="calc-button" @click="buttonClick('1')">1</div>
        <div class="calc-button" @click="buttonClick('2')">2</div>
        <div class="calc-button" @click="buttonClick('3')">3</div>
        <div class="calc-button" @click="buttonClick('+')">
          <plus-icon size="1.1x" class="custom-class"></plus-icon>
        </div>
        <div class="calc-button long" @click="buttonClick('0')">0</div>
        <div class="calc-button" @click="buttonClick('•')">•</div>
        <div class="calc-button" @click="buttonClick('=')">=</div>
      </div>
    </div>
  </div>
</template>

<script>
import { DollarSignIcon, PlusIcon, MinusIcon, XIcon } from "vue-feather-icons";
export default {
  name: "BasicCalculator",
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
        }
        this.operator = "+";
      } else if (number == "-") {
        if (this.calcText != "") {
          this.nums.push(this.calcText);
          this.calcText = "";
        }
        this.operator = "-";
      } else if (number == "x") {
        if (this.calcText != "") {
          this.nums.push(this.calcText);
          this.calcText = "";
        }
        this.operator = "x";
      } else if (number == "/") {
        if (this.calcText != "") {
          this.nums.push(this.calcText);
          this.calcText = "";
        }
        this.operator = "/";
      } else if (number == "ac") {
        this.calcText = "";
        this.nums = [];
        this.operator = "";
      } else if (number == "=") {
        if (this.calcText != "" && this.nums.length >= 1) {
          this.nums.push(this.calcText);
          this.calcText = "";
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
      } else if (number == "•") {
        if (!this.calcText.includes(".")) {
          this.calcText += ".";
        }
      } else if (number == "%") {
        if (!this.calcText == "") {
          this.calcText = parseFloat(this.calcText) * 0.01;
        }
      } else {
        this.calcText += number;
      }
    }
  },
  components: {
    PlusIcon,
    DollarSignIcon,
    MinusIcon,
    XIcon
  }
};
</script>

<style lang="scss" scoped>
.calculator {
  width: 340px;
  position: relative;

  h1 {
    text-align: right;
    color: white;
    margin: 10px;
  }

  .empty {
    text-align: right;
    margin: 19px 0;
  }

  .buttons {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;

    .calc-button {
      height: 68px;
      width: 70px;
      background: #151e2b;
      display: flex;
      justify-content: center;
      align-items: center;
      margin: 5px 5px;
      color: #eaeaea;
      font-weight: 600;
      font-size: 1.4rem;
      border-bottom: solid 2px #364357;

      &:hover {
        background: #6c63ff;
        cursor: pointer;
      }
    }

    .long {
      width: 156px;
    }
  }
}
</style>