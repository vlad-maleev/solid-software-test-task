<template>
  <div id="app">
    <div class="greeting">
      <p
        aria-label="&quot;Click&quot; to change color or &quot;Alt+Click&quot; to change font"
        data-balloon-pos="up"
        :style="greetingStyle"
        @click.exact="changeColor"
        @click.alt="changeFontFamily"
      >{{ greeting }}</p>
    </div>

    <div class="infoContainer">
      <div class="row">
        <p class="value">
          <span class="title">Color:</span>
          {{ greetingStyle.color }}
        </p>
      </div>

      <div class="row">
        <p class="value">
          <span class="title">Font:</span>
          {{ greetingStyle.fontFamily }}
        </p>
      </div>
    </div>
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
      let fontFamilies = [
        "Audiowide",
        "Gloria Hallelujah",
        "Lobster Two",
        "Miniver",
        "Oswald",
        "Saira Stencil One"
      ];

      this.greetingStyle.fontFamily =
        fontFamilies[Math.floor(Math.random() * fontFamilies.length)];
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Rubik|Poppins|Audiowide|Gloria+Hallelujah|Lobster+Two|Miniver|Oswald|Saira+Stencil+One&display=swap");

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
  flex-direction: column;
}

.greeting p {
  font-size: 96px;
  cursor: pointer;
}

.infoContainer {
  display: flex;
  flex-direction: row;
}

.infoContainer .row {
  margin: -80px 20px;
}

.infoContainer .title {
  color: rgb(125, 125, 131);
  font-weight: normal;
}

.infoContainer .value {
  font-size: 26px;
  font-weight: bold;
  font-family: "Poppins";
  color: rgb(37, 37, 43);
}

/* Balloon CSS Library */
:root {
  --balloon-color: rgba(238, 238, 238, 0.95);
  --balloon-font-size: 14px;
  --balloon-move: 4px;
}

button[aria-label][data-balloon-pos] {
  overflow: visible;
}

[aria-label][data-balloon-pos] {
  position: relative;
  cursor: pointer;
}
[aria-label][data-balloon-pos]:after {
  opacity: 0;
  pointer-events: none;
  transition: all 0.18s ease-in-out 0.18s;
  text-indent: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  font-weight: normal;
  font-style: normal;
  text-shadow: none;
  font-size: var(--balloon-font-size);
  background: var(--balloon-color);
  border-radius: 2px;
  color: rgb(54, 54, 59);
  content: attr(aria-label);
  padding: 0.5em 1em;
  position: absolute;
  white-space: nowrap;
  z-index: 10;
}
[aria-label][data-balloon-pos]:before {
  width: 0;
  height: 0;
  border: 5px solid transparent;
  border-top-color: var(--balloon-color);
  opacity: 0;
  pointer-events: none;
  transition: all 0.18s ease-out 0.18s;
  content: "";
  position: absolute;
  z-index: 10;
}
[aria-label][data-balloon-pos]:hover:before,
[aria-label][data-balloon-pos]:hover:after,
[aria-label][data-balloon-pos][data-balloon-visible]:before,
[aria-label][data-balloon-pos][data-balloon-visible]:after,
[aria-label][data-balloon-pos]:not([data-balloon-nofocus]):focus:before,
[aria-label][data-balloon-pos]:not([data-balloon-nofocus]):focus:after {
  opacity: 1;
  pointer-events: none;
}
[aria-label][data-balloon-pos].font-awesome:after {
  font-family: FontAwesome, -apple-system, BlinkMacSystemFont, "Segoe UI",
    Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
}
[aria-label][data-balloon-pos][data-balloon-break]:after {
  white-space: pre;
}
[aria-label][data-balloon-pos][data-balloon-break][data-balloon-length]:after {
  white-space: pre-line;
  word-break: break-word;
}
[aria-label][data-balloon-pos][data-balloon-blunt]:before,
[aria-label][data-balloon-pos][data-balloon-blunt]:after {
  transition: none;
}
[aria-label][data-balloon-pos][data-balloon-pos="up"]:after {
  bottom: 100%;
  left: 50%;
  margin-bottom: 10px;
  transform: translate(-50%, var(--balloon-move));
  transform-origin: top;
}
[aria-label][data-balloon-pos][data-balloon-pos="up"]:before {
  bottom: 100%;
  left: 50%;
  transform: translate(-50%, var(--balloon-move));
  transform-origin: top;
}
[aria-label][data-balloon-pos][data-balloon-pos="up"]:hover:after,
[aria-label][data-balloon-pos][data-balloon-pos="up"][data-balloon-visible]:after {
  transform: translate(-50%, 0);
}
[aria-label][data-balloon-pos][data-balloon-pos="up"]:hover:before,
[aria-label][data-balloon-pos][data-balloon-pos="up"][data-balloon-visible]:before {
  transform: translate(-50%, 0);
}
</style>
