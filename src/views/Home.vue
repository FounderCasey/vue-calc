<template>
  <div id="home">
    <div class="container">
      <h1>Calculated</h1>
      <div class="wrapper">
        <p>Select your calculator</p>
        <div class="flexbox">
          <input type="radio" name="calc" id="basic" value="basic" checked v-model="selected" />
          <label for="basic" class="item">
            <plus-icon size="1.75x" class="custom-class"></plus-icon>
          </label>
          <input type="radio" name="calc" id="size_2" value="1" v-model="selected" />
          <label for="size_2" class="item">
            <clock-icon size="1.75x" class="custom-class"></clock-icon>
          </label>
          <input type="radio" name="calc" id="size_3" value="2" v-model="selected" />
          <label for="size_3" class="item">
            <clock-icon size="1.75x" class="custom-class"></clock-icon>
          </label>
          <input type="radio" name="calc" id="size_4" value="3" v-model="selected" />
          <label for="size_4" class="item">
            <clock-icon size="1.75x" class="custom-class"></clock-icon>
          </label>
          <input type="radio" name="calc" id="size_5" value="4" v-model="selected" />
          <label for="size_5" class="item">
            <clock-icon size="1.75x" class="custom-class"></clock-icon>
          </label>
          <input type="radio" name="calc" id="size_6" value="5" v-model="selected" />
          <label for="size_6" class="item">
            <clock-icon size="1.75x" class="custom-class"></clock-icon>
          </label>
          <input type="radio" name="calc" id="size_7" value="6" v-model="selected" />
          <label for="size_7" class="item">
            <clock-icon size="1.75x" class="custom-class"></clock-icon>
          </label>
          <input type="radio" name="calc" id="size_8" value="7" v-model="selected" />
          <label for="size_8" class="item">
            <clock-icon size="1.75x" class="custom-class"></clock-icon>
          </label>
        </div>
      </div>
    </div>
    <div class="calculator-container">
      <BasicCalculator v-if="selected == 'basic'"></BasicCalculator>
      <h1 v-if="selected != 'basic'">This calculator is coming soon!</h1>
    </div>
  </div>
</template>

<script>
import {
  DollarSignIcon,
  PlusIcon,
  MinusIcon,
  XIcon,
  ClockIcon
} from "vue-feather-icons";
import { constants } from "crypto";
import { parse } from "path";

import BasicCalculator from "../components/BasicCalculator";

export default {
  data() {
    return {
      selected: "basic"
    };
  },
  methods: {},
  components: {
    PlusIcon,
    DollarSignIcon,
    MinusIcon,
    XIcon,
    ClockIcon,
    BasicCalculator
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

    input[type="radio"] {
      display: none;
    }

    input[type="radio"]:checked + label {
      background-color: #6c63ff;
    }

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
        cursor: pointer;
      }
    }
  }
}
</style>