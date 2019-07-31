<template>
  <div id="app">
    <p
      :style="greetingStyle"
      @click.exact="changeColor"
      @click.alt="changeFontFamily"
    >{{ greeting }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      greeting: "Hey there",
      greetingStyle: {
        color: "red",
        fontFamily: "Avenir"
      }
    };
  },
  methods: {
    changeColor() {
      var letters = "0123456789ABCDEF";
      var color = "#";
      for (var i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
      }

      this.greetingStyle.color = color;
    }
  }
};
</script>

<style>
body {
  height: 90vh;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: inherit;
  display: flex;
  justify-content: center;
  align-items: center;
}

p {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  font-size: 40px;
  cursor: pointer;
}
</style>
