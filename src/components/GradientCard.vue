<template>
  <div class="card relative p-6" style="--rotation: 0deg;" ref="card" @mousemove="handleMousemoveEvent">
    <div class="z-[2] relative">
      <slot/>
    </div>
  </div>
</template>

<script setup>
import {ref, onMounted} from "vue"

const card = ref()

const handleMousemoveEvent = evt => {
  // evt.stopPropagation()
  evt.stopImmediatePropagation()
  const cardCoordinates = {
    x: card.value.offsetLeft + card.value.offsetWidth / 2,
    y: card.value.offsetTop + card.value.offsetHeight / 2
  }

  requestAnimationFrame(_ => {
    const mouseCoordinates = {x: evt.pageX, y: evt.pageY}
    let gapX = cardCoordinates.x - mouseCoordinates.x
    let gapY = cardCoordinates.y - mouseCoordinates.y
    let angleInRadians = Math.atan2(gapY, gapX)
    const rotation = Math.round(angleInRadians * (180 / Math.PI))

    card.value.style.setProperty(`--rotation`, `${rotation - 90}deg`)
  })
}

onMounted(_ => {

})
</script>

<style scoped lang="scss">
.card {
  --gradient-color-two: #B61CFF;
  --gradient-color-one: #215DEE;
  background: #28272c;
  @apply rounded-2xl;

  &:before {
    content: "";
    position: absolute;
    background: 0 0;
    inset: 0;
    z-index: 1;
    opacity: 0;
    transition: opacity .25s;
    background: linear-gradient(var(--rotation), transparent 60%, var(--gradient-color-one) 70%, var(--gradient-color-two) 90%);
    @apply rounded-2xl;
  }

  &:after {
    content: "";
    position: absolute;
    inset: 1px;
    z-index: 1;
    background: #17171C;
    @apply rounded-2xl;
  }

  &:hover:before {
    opacity: 1;
  }
}
</style>
