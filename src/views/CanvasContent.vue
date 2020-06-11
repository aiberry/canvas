<template>
  <div class="about">
    <h1>This is an canvas page</h1>
    <CanvasField></CanvasField>
  </div>
</template>

<script>
import CanvasField from "@/components/CanvasField.vue";

export default {
  name: "CanvasContent",

  components: {
    CanvasField,
  },
};
</script>
