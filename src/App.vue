<template>
  <div class="p-10 grid gap-10 grid-cols-4">
    <template v-for="i in 10">
      <GradientCard>
        <img
            :src="img"
            class="rounded-2xl"
        />
      </GradientCard>
    </template>
  </div>
</template>

<script setup>
import {ref} from "vue"
import GradientCard from "@/components/GradientCard.vue";

const img = ref('https://images.unsplash.com/photo-1500917293891-ef795e70e1f6?crop=entropy&cs=tinysrgb&fit=max&fm=webp&ixid=M3wxMTc3M3wwfDF8c2VhcmNofDI4fHxmYXNoaW9uJTIwYmVhdXR5fGVufDB8fHx8MTY5MjQ0NTA2MHww&ixlib=rb-4.0.3&q=80&w=2000')
</script>


<style lang="scss">
body {
  background-color: #100F15
}
</style>
