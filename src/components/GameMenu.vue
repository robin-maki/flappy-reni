<script lang="ts" setup>
import { SCALE_MODES, Texture } from "pixi.js";
import { ref } from "vue";
import logoPNG from "../assets/sprites/flappyreni.png";
import { useElementHoverScale } from "../composables/useElementHoverScale";
import { useCosineAmplitude } from "../composables/useCosineAmplitude";

const emit = defineEmits(["start"]);

const texture = Texture.from(logoPNG, {
  scaleMode: SCALE_MODES.NEAREST,
});

const containerRef = ref();

const offsetY = useCosineAmplitude();
const scale = useElementHoverScale(containerRef);
</script>

<template>
  <container
    ref="containerRef"
    :x="320"
    :y="180"
    :scale="0.15"
    @click="emit('start')"
    @touchstart="emit('start')">
    <sprite :y="offsetY" :texture="texture" :anchor="0.5" :scale="scale" />
  </container>
</template>

<style lang="scss" scoped></style>
