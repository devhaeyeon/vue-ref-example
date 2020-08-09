<template>
  <div>
    <form>
      <fieldset>
        <legend>라디오 박스 커스텀 폼</legend>
        <div class="comp-input">
          <strong>라디오 박스</strong>
          <div calss="continer-radio">
            <input
              type="radio"
              id="inpRadio1"
              class="input-radio"
              name="radio"
              value="one"
              v-model="radioTxt"
              @change="changedRadio"
            >
            <label for="inpRadio1" class="radio-label">라디오 박스 선택1</label>
          </div>
          <div calss="continer-radio">
            <input
              type="radio"
              id="inpRadio2"
              class="input-radio"
              name="radio"
              value="two"
              v-model="radioTxt"
              @click="changedRadio"
            >
            <label for="inpRadio2" class="radio-label">라디오 박스 선택2</label>
          </div>
          <input type="text" class="input-text" ref="inputRef">
        </div>
        <p class="error" v-if="isShowRadioError">라디오 박스 값을 선택해주세요.</p>
      </fieldset>
    </form>
  </div>
</template>

<style>
.error {
  color: red;
}
.input-radio {
  width: 18px;
  height: 18px;
}
.input-radio::focus {
  border: 1px solid blue;
}
.input-radio + .radio-label {
  position: relative;
  display: inline-block;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.input-radio + .radio-label::before {
  position: absolute;
  top: 0;
  left: -25px;
  display: inline-block;
  margin: -2px 8px 0 0;
  width: 18px;
  height: 18px;
  line-height: 18px;
  text-align: center;
  vertical-align: middle;
  background-color: #fafafa;
  border: 1px solid #cacece;
  border-radius: 100%;
  box-shadow: 0px 1px 2px;
  content: "";
}
.input-radio + .radio-label:active::before,
.input-radio:checked + .radio-label:active::before {
  box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.05);
}
.input-radio:checked + .radio-label::before {
  color: #314ca2;
  text-shadow: 1px 1px #fff;
  background-color: #f1f1f1;
  border-color: #adb8c0;
  box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.05);
  content: "o";
}
</style>
<script>
export default {
  name: "FormComp",
  data() {
    return {
      radioTxt: "",
      isShowRadioError: this.radioTxt === null
    };
  },
  methods: {
    checkRadio() {
      console.log(this.radioTxt);
      if (this.radioTxt) {
        this.isShowRadioError = false;
        return this.radioTxt;
      } else {
        this.isShowRadioError = true;
        return undefined;
      }
    },
    changedRadio() {
      this.isShowRadioError = false;
    },
    focusInput() {
      const el = this.$refs.inputRef.$el;
      this.$refs.inputRef.focus();
      console.log("----inputRef---");
      console.log(el);
      console.log(this.$refs.inputRef.classList);
    }
  }
};
</script>