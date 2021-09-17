<template>
  <div class="bglines"></div>
</template>

<script>
import { randomWithin, randomFrom } from "../functions/Random";
export default {
  mounted() {
    this.initBg();
  },
  methods: {
    initBg() {
      const bg = document.querySelector(".bglines");
      this.createLines(
        bg,
        ["#131c38", "#201a33", "#23285e", "#1d1c47", "#2e1657"],
        20
      );
    },
    createLines(parent, colors, count) {
      const elms = new Array(count)
        .fill(0)
        .map(() => document.createElement("div"));
      elms.forEach((el) => {
        const st = el.style;
        st.position = "absolute";
        st.left = "-50%";
        st.top = `${randomWithin(0, 100)}%`;
        st.width = "200%";
        st.height = `${randomWithin(3, 20)}%`;
        st.transform = `rotate(${randomWithin(-20, 20)}deg)`;
        st.opacity = `${randomWithin(0.1, 0.5)}`;
        st.backgroundColor = randomFrom(colors);
        st.mixBlendMode = "darken";
        parent.appendChild(el);
      });
    },
  },
};
</script>

<style>
.bglines {
  position: absolute;
  width: 100%;
  height: 100%;
  overflow: hidden;
  background-image: linear-gradient(
    to top,
    rgba(89, 55, 110, 1) 0%,
    rgba(56, 25, 103, 1) 28%,
    rgba(32, 42, 74, 1) 100%
  );
}
</style>
