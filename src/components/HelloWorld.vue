<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <FormComp ref="formChildRef"/>
    <div @click="focusDomInputRef">Input Focus</div>
  </div>
</template>

<script>
import FormComp from "@/components/FormComp";
export default {
  name: "HelloWorld",
  components: {
    FormComp
  },
  props: {
    msg: String
  },
  methods: {
    focusDomInputRef() {
      const el = this.$refs.formChildRef.$el;
      console.log("---formChildRef---");
      console.log(el);
      this.$refs.formChildRef.focusInput();
    },
    checkRadio() {
      return this.$refs.formChildRef.checkRadio();
    }
  },
  mounted() {
    // this.getRadioRef();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
