<script setup>
const images = [
  { src: '/img/FOTO 4.jpeg', alt: 'Recepción de la Clínica San Jorge', span: 'col-span-2 row-span-2' },
  { src: '/img/FOTO 39.jpeg', alt: 'Sala de espera moderna', span: 'col-span-1 row-span-1' },
  { src: '/img/FOTO 8.jpeg', alt: 'Consultorio médico', span: 'col-span-1 row-span-1' },
  { src: '/img/FOTO 37.jpeg', alt: 'Área de laboratorio', span: 'col-span-1 row-span-1' },
  { src: '/img/FOTO 13.jpeg', alt: 'Sala de procedimientos', span: 'col-span-1 row-span-1' },
  { src: '/img/FOTO 32.jpeg', alt: 'Equipo médico avanzado', span: 'col-span-1 row-span-1' },
  { src: '/img/FOTO 12.jpeg', alt: 'Área de imagenología', span: 'col-span-1 row-span-1' },
  { src: '/img/FOTO 7.jpeg', alt: 'Espacio de recuperación', span: 'col-span-2 row-span-1' },
  { src: '/img/FOTO 34.jpeg', alt: 'Instalaciones exteriores', span: 'col-span-1 row-span-1' }
]

const currentIndex = ref(0)
const lightboxOpen = ref(false)

function openLightbox(index) {
  currentIndex.value = index
  lightboxOpen.value = true
}

function prev() {
  currentIndex.value = currentIndex.value === 0 ? images.length - 1 : currentIndex.value - 1
}

function next() {
  currentIndex.value = currentIndex.value === images.length - 1 ? 0 : currentIndex.value + 1
}

const sectionVisible = ref(false)
onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          sectionVisible.value = true
          observer.disconnect()
        }
      })
    },
    { threshold: 0.05 }
  )
  const el = document.getElementById('instalaciones')
  if (el) observer.observe(el)
})
</script>

<template>
  <section
    id="instalaciones"
    class="py-28 lg:py-36 bg-clinic-light relative overflow-hidden"
  >
    <div class="absolute top-0 right-0 w-100 h-100 bg-clinic-accent/20 rounded-full blur-[120px] pointer-events-none" />

    <div class="container mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div
        :class="[
          'text-center mb-20 transition-all duration-800 ease-out',
          sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
        ]"
      >
        <div class="inline-flex items-center gap-2 bg-clinic-primary/5 rounded-full px-4 py-1.5 mb-6">
          <div class="w-1.5 h-1.5 bg-clinic-primary rounded-full" />
          <span class="text-clinic-primary text-sm font-semibold tracking-wide uppercase">Instalaciones</span>
        </div>
        <h2
          class="font-heading text-3xl sm:text-4xl lg:text-5xl font-bold text-clinic-dark mb-5"
          style="text-wrap: balance;"
        >
          Espacios diseñados para <span class="gradient-text">tu bienestar</span>
        </h2>
        <p class="text-lg text-clinic-gray max-w-2xl mx-auto">
          Tecnología avanzada y ambientes cómodos para la mejor experiencia.
        </p>
      </div>

      <div class="grid grid-cols-2 lg:grid-cols-3 gap-4 lg:gap-5 auto-rows-50 lg:auto-rows-60">
        <div
          v-for="(image, index) in images"
          :key="index"
          :class="[
            'facility-img relative rounded-2xl lg:rounded-3xl overflow-hidden cursor-pointer group',
            image.span,
            sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-6'
          ]"
          :style="{ transitionDelay: `${150 + index * 80}ms` }"
          @click="openLightbox(index)"
        >
          <img
            :src="image.src"
            :alt="image.alt"
            class="w-full h-full object-cover"
            loading="lazy"
          >
          <div class="absolute inset-0 bg-clinic-dark/0 group-hover:bg-clinic-dark/20 transition-all duration-400 flex items-center justify-center">
            <div class="w-11 h-11 bg-white/80 backdrop-blur-sm rounded-full flex items-center justify-center opacity-0 group-hover:opacity-100 scale-75 group-hover:scale-100 transition-all duration-300 shadow-lg">
              <UIcon
                name="i-lucide-expand"
                class="w-4 h-4 text-clinic-dark"
              />
            </div>
          </div>
        </div>
      </div>
    </div>

    <UModal
      v-model:open="lightboxOpen"
      :ui="{ content: 'max-w-5xl' }"
    >
      <template #body>
        <div class="relative">
          <img
            :src="images[currentIndex].src"
            :alt="images[currentIndex].alt"
            class="w-full h-auto max-h-[75vh] object-contain rounded-2xl"
          >
          <UButton
            icon="i-lucide-chevron-left"
            color="white"
            variant="solid"
            size="lg"
            class="absolute left-3 top-1/2 -translate-y-1/2 rounded-full shadow-lg"
            @click="prev"
          />
          <UButton
            icon="i-lucide-chevron-right"
            color="white"
            variant="solid"
            size="lg"
            class="absolute right-3 top-1/2 -translate-y-1/2 rounded-full shadow-lg"
            @click="next"
          />
          <div class="flex justify-center gap-1.5 mt-4">
            <div
              v-for="(_, i) in images"
              :key="i"
              :class="[
                'w-2 h-2 rounded-full transition-all duration-300 cursor-pointer',
                i === currentIndex ? 'bg-clinic-primary w-6' : 'bg-clinic-muted'
              ]"
              @click="currentIndex = i"
            />
          </div>
        </div>
      </template>
    </UModal>
  </section>
</template>
