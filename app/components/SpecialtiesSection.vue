<script setup>
const featured = [
  { icon: 'i-lucide-heart-pulse', name: 'Cardiología', image: '/img/FOTO 23.jpeg' },
  { icon: 'i-lucide-baby', name: 'Pediatría', image: '/img/FOTO 24.jpeg' },
  { icon: 'i-lucide-brain', name: 'Neurología', image: '/img/FOTO 28.jpeg' },
  { icon: 'i-lucide-circle-dot', name: 'Gastroenterología', image: '/img/FOTO 29.jpeg' }
]

const marqueeItems = [
  'Dermatología', 'Reumatología', 'Neumología', 'Gineco-Obstetricia',
  'Otorrinolaringología', 'Hematología', 'Infectología', 'Endocrinología',
  'Medicina Física', 'Ecografía', 'Alergología', 'Proctología'
]

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
  const el = document.getElementById('especialidades')
  if (el) observer.observe(el)
})
</script>

<template>
  <section
    id="especialidades"
    class="relative overflow-hidden"
  >
    <div class="relative py-28 lg:py-36">
      <div class="absolute inset-0">
        <img
          src="/img/FOTO 10.jpeg"
          alt=""
          class="w-full h-full object-cover"
          loading="lazy"
        >
        <div class="absolute inset-0 bg-clinic-dark/85" />
      </div>

      <div class="absolute top-0 left-0 w-150 h-150 bg-clinic-primary/8 rounded-full blur-[150px] pointer-events-none" />
      <div class="absolute bottom-0 right-0 w-100 h-100 bg-clinic-secondary/8 rounded-full blur-[120px] pointer-events-none" />

      <div class="container mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
        <div
          :class="[
            'text-center mb-20 transition-all duration-800 ease-out',
            sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
        >
          <div class="inline-flex items-center gap-2 bg-clinic-secondary/10 rounded-full px-4 py-1.5 mb-6 border border-clinic-secondary/20">
            <div class="w-1.5 h-1.5 bg-clinic-secondary rounded-full" />
            <span class="text-clinic-secondary text-sm font-semibold tracking-wide uppercase">Especialidades</span>
          </div>
          <h2
            class="font-heading text-3xl sm:text-4xl lg:text-5xl font-bold text-white mb-5"
            style="text-wrap: balance;"
          >
            Equipo <span class="text-clinic-secondary">multidisciplinario</span>
          </h2>
          <p class="text-lg text-gray-400 max-w-2xl mx-auto">
            Especialistas comprometidos con tu bienestar integral.
          </p>
        </div>

        <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-5 mb-20">
          <div
            v-for="(spec, index) in featured"
            :key="index"
            :class="[
              'group relative rounded-3xl overflow-hidden h-70 cursor-pointer',
              sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
            ]"
            :style="{ transitionDelay: `${200 + index * 120}ms` }"
          >
            <img
              :src="spec.image"
              :alt="spec.name"
              class="absolute inset-0 w-full h-full object-cover transition-transform duration-700 group-hover:scale-110"
              loading="lazy"
            >
            <div class="absolute inset-0 bg-linear-to-t from-clinic-dark/80 to-clinic-dark/10 group-hover:from-clinic-primary/70 transition-all duration-500" />

            <div class="absolute bottom-0 left-0 right-0 p-6">
              <div class="w-11 h-11 bg-white/10 backdrop-blur-sm rounded-xl flex items-center justify-center mb-3 border border-white/10 group-hover:scale-110 transition-transform duration-300">
                <UIcon
                  :name="spec.icon"
                  class="w-5 h-5 text-clinic-secondary"
                />
              </div>
              <h3 class="font-heading font-bold text-white text-lg">
                {{ spec.name }}
              </h3>
            </div>
          </div>
        </div>

        <!-- <div
          :class="[
            'transition-all duration-800 ease-out delay-500',
            sectionVisible ? 'opacity-100' : 'opacity-0'
          ]"
        >
          <UMarquee
            :pause-on-hover="true"
            :repeat="3"
          >
            <div
              v-for="(item, index) in marqueeItems"
              :key="index"
              class="specialty-chip flex items-center gap-2 bg-white/5 backdrop-blur-sm border border-white/10 rounded-full px-5 py-2.5 mx-2"
            >
              <div class="w-2 h-2 bg-clinic-secondary/60 rounded-full" />
              <span class="text-white/80 text-sm font-medium whitespace-nowrap">{{ item }}</span>
            </div>
          </UMarquee>
        </div> -->
      </div>
    </div>
  </section>
</template>
