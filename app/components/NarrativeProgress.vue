<script setup>
const props = defineProps({
  scenes: {
    type: Array,
    required: true
  },
  activeScene: {
    type: Number,
    required: true
  },
  progress: {
    type: Number,
    required: true
  }
})

function scrollToScene(index) {
  const section = document.getElementById('narrativa')
  if (!section) return
  const sceneHeight = section.offsetHeight / props.scenes.length
  const target = section.offsetTop + sceneHeight * index
  window.scrollTo({ top: target, behavior: 'smooth' })
}
</script>

<template>
  <div class="absolute right-6 top-1/2 -translate-y-1/2 z-40 hidden lg:flex flex-col items-center gap-0">
    <div class="relative flex flex-col items-center">
      <div class="absolute top-0 bottom-0 w-px bg-white/10" />
      <div
        class="absolute top-0 w-px bg-clinic-secondary transition-all duration-500 ease-out"
        :style="{ height: `${progress * 100}%` }"
      />

      <button
        v-for="(scene, index) in scenes"
        :key="index"
        class="relative flex items-center gap-3 py-4 group cursor-pointer"
        @click="scrollToScene(index)"
      >
        <div
          :class="[
            'w-3 h-3 rounded-full border-2 transition-all duration-500 shrink-0',
            index < activeScene
              ? 'bg-clinic-secondary border-clinic-secondary scale-100'
              : index === activeScene
                ? 'bg-clinic-secondary border-clinic-secondary scale-125 shadow-lg shadow-clinic-secondary/40'
                : 'bg-transparent border-white/20 scale-100'
          ]"
        />

        <span
          :class="[
            'text-xs font-medium transition-all duration-500 whitespace-nowrap',
            index === activeScene
              ? 'opacity-100 translate-x-0 text-white'
              : index < activeScene
                ? 'opacity-60 translate-x-0 text-clinic-secondary'
                : 'opacity-0 -translate-x-2 text-white/40'
          ]"
        >
          {{ scene.service }}
        </span>
      </button>
    </div>
  </div>
</template>
