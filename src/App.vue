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
      let letters = "0123456789ABCDEF";
      let color = "#";

      for (let i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
      }

      this.greetingStyle.color = color;
    },
    changeFontFamily() {
      let fontFamilies = ['Audiowide', 'Gloria Hallelujah', 'Lobster Two', 'Miniver', 'Oswald', 'Saira Stencil One'];

      this.greetingStyle.fontFamily = fontFamilies[Math.floor(Math.random() * fontFamilies.length)];
    }
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Audiowide|Gloria+Hallelujah|Lobster+Two|Miniver|Oswald|Saira+Stencil+One&display=swap');

body {
  height: 90vh;
  background-color: azure
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
  font-size: 40px;
  cursor: pointer;
}
</style>
