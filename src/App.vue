<template>
  <div id="app">
    <img width="25%" src="./assets/logo.png">
    <HelloWorld msg="Hello Vue in CodeSandbox!" ref="formChildRef"/>
    <button type="button" @click="submitRadioValue">라디오 박스 선택값 전송</button>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  components: {
    HelloWorld
  },
  methods: {
    submitRadioValue() {
      const radioValue = this.$refs.formChildRef.checkRadio();
      if (!radioValue) return;
      alert(`라디오 박스 값 ${radioValue}이 전송 되었습니다.`);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
