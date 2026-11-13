<script setup lang="ts">
// Bubbles from public/favicon.svg without the tile. The gap between them is
// cut out with a mask, so it shows whatever background the logo sits on.
import { useId } from "vue";

withDefaults(defineProps<{ width?: number }>(), { width: 30 });
const maskId = useId();
const front =
  "M188 106h-76a30 30 0 0 0-30 30v24a30 30 0 0 0 30 30h52l30 26-4-27a30 30 0 0 0 28-29v-24a30 30 0 0 0-30-30z";
</script>

<template>
  <svg
    :width="width"
    :height="Math.round((width * 160) / 182)"
    viewBox="37 57 182 160"
    aria-hidden="true"
  >
    <mask
      :id="maskId"
      maskUnits="userSpaceOnUse"
      x="0"
      y="0"
      width="256"
      height="256"
    >
      <rect x="0" y="0" width="256" height="256" fill="white" />
      <path
        :d="front"
        fill="none"
        stroke="black"
        stroke-width="10"
        stroke-linejoin="round"
      />
    </mask>
    <g :mask="`url(#${maskId})`">
      <path
        d="M68 58h88a30 30 0 0 1 30 30v26a30 30 0 0 1-30 30H92l-30 26 4-27a30 30 0 0 1-28-29V88a30 30 0 0 1 30-30z"
        fill="#eabf7d"
      />
      <path :d="front" fill="#db9a59" />
    </g>
  </svg>
</template>
