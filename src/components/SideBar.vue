<template>
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
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
      </div>
    </div>
  </div>
</template>

<script>
import { DollarSignIcon, PlusIcon } from "vue-feather-icons";

export default {
  name: "SideBar",
  components: {
    PlusIcon,
    DollarSignIcon
  }
};
</script>

<style lang="scss">
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