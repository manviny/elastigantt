<template>
<svg class="elastigantt__info"
    :x="getX"
    :y="task.y"
    :width="getWidth"
    :height="root.state.row.height"
    xmlns="http://www.w3.org/2000/svg">
  <rect x="0" y="0" width="100%" height="100%" :style="root.state.info.style"></rect>
  <text x="50%" y="50%" :style="getTextStyle" text-anchor="middle" alignment-baseline="middle">{{task.label}}</text>
</svg>
</template>
<script>
export default {
  inject: ['root'],
  props: ['task'],
  data() {
    return {};
  },
  computed: {
    getX() {
      const state = this.root.state;
      this.root.state.ctx.font = `${root.state.info.fontWeight} ${root.state.info.fontSize} ${root.state.info.fontFamily}`;
      const textWidth = this.root.state.ctx.measureText(this.task.label).width / 2 + 10;
      return this.task.x + this.task.width / 2 - textWidth;
    },
    getWidth() {
      return this.root.state.ctx.measureText(this.task.label).width + 20;
    },
    getTextStyle() {
      let state = this.root.state;
      return `${root.state.info.textStyle};font-family:${root.state.info.fontFamily};font-size:${
            root.state.info.fontSize};font-weight:${root.state.info.fontWeight};`;
    }
  }
}
</script>
