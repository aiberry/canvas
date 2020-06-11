<template>
  <div class="hello">
    <h2>Canvas component</h2>
    <canvas
      ref="canvas"
      @mousedown="onMouseDown"
      @mousemove="onMouseMove"
      @mouseup="onMouseUp"
      width="500"
      height="500"
    ></canvas>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import axios from "axios";

@Component
export default class CanvasField extends Vue {
  @Prop() private image;

  mouseDownX = 0;
  mouseDownY = 0;
  positionForMoving = false;
  imagePromice;

  drawCanvas(fillColor, rectX = 225, rectY = 225, rectSizeX = 50, rectSizeY = 50) {
    const ctx = this.$refs.canvas.getContext("2d");
    const canvasImage = new Image();
    canvasImage.onload = () => {
      ctx.drawImage(canvasImage, 0, 0);
      ctx.fillStyle = fillColor;
      ctx.fillRect(rectX, rectY, rectSizeX, rectSizeY);
    };
    this.imagePromice.then((image) => {
      canvasImage.src = image;
      return image;
    }, console.log);
  }

  onMouseDown(e) {
    if (225 < e.offsetX && e.offsetX < 275 && 225 < e.offsetY && e.offsetY < 275) {
      this.mouseDownX = e.offsetX;
      this.mouseDownY = e.offsetY;
      this.positionForMoving = true;
      this.drawCanvas("rgba(0, 0, 200, 0.5)");
    }
  }

  onMouseMove(e) {
    if (this.positionForMoving) {
      this.drawCanvas(
        "rgba(0, 0, 200, 0.5)",
        225 + (e.offsetX - this.mouseDownX),
        225 + (e.offsetY - this.mouseDownY),
      );
    }
  }

  onMouseUp() {
    this.positionForMoving = false;
    this.drawCanvas("rgba(0, 200, 0, 0.5)");
  }

  mounted() {
    this.imagePromice = axios
      .get("http://fantogramma.org/test.png", {
        responseType: "arraybuffer",
      })
      .then((response) => Buffer.from(response.data, "binary").toString("base64"))
      .then((img) => `data:image/png;base64, ${img}`)
      .then((imageStr) => {
        const ctx = this.$refs.canvas.getContext("2d");
        const canvasImage = new Image();
        canvasImage.onload = () => {
          ctx.drawImage(canvasImage, 0, 0);
          ctx.fillStyle = "rgba(0, 200, 0, 0.5)";
          ctx.fillRect(225, 225, 50, 50);
        };
        canvasImage.src = imageStr;
        return imageStr;
      }, console.log);
  }
}
</script>

<style scoped lang="scss">
canvas {
  border: 1px solid #f00;
}
</style>
