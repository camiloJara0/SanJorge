<script setup>
const features = [
  { icon: 'i-lucide-user-round-check', title: 'Atención Humanizada', description: 'Trato cálido y respetuoso en cada interacción.', image: '/img/FOTO 11.jpeg', large: true },
  { icon: 'i-lucide-microscope', title: 'Tecnología Avanzada', description: 'Equipos de última generación para diagnósticos precisos.', image: '/img/FOTO 26.jpeg', large: false },
  { icon: 'i-lucide-users', title: 'Personal Especializado', description: 'Equipo médico altamente calificado y comprometido.', image: '/img/FOTO 32.jpeg', large: false },
  { icon: 'i-lucide-shield-check', title: 'Cobertura Integral', description: 'Medicina general, especialidades, laboratorio y más.', image: '/img/FOTO 31.jpeg', large: false },
  { icon: 'i-lucide-clock-4', title: 'Disponibilidad 24/7', description: 'Transporte y emergencia disponibles todo el día.', image: '/img/FOTO 12.jpeg', large: true },
  { icon: 'i-lucide-map-pin', title: 'Ubicación Estratégica', description: 'Instalaciones modernas y accesibles en Cali.', image: '/img/FOTO 1.jpeg', large: false }
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
  const el = document.getElementById('por-que')
  if (el) observer.observe(el)
})
</script>

<template>
  <section
    id="por-que"
    class="py-28 lg:py-36 relative overflow-hidden"
  >
    <div class="absolute top-0 left-0 w-125 h-125 bg-clinic-accent/15 rounded-full blur-[120px] pointer-events-none" />

    <div class="container mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div
        :class="[
          'text-center mb-20 transition-all duration-800 ease-out',
          sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
        ]"
      >
        <div class="inline-flex items-center gap-2 bg-clinic-primary/5 rounded-full px-4 py-1.5 mb-6">
          <div class="w-1.5 h-1.5 bg-clinic-primary rounded-full" />
          <span class="text-clinic-primary text-sm font-semibold tracking-wide uppercase">Diferenciales</span>
        </div>
        <h2
          class="font-heading text-3xl sm:text-4xl lg:text-5xl font-bold text-clinic-dark mb-5"
          style="text-wrap: balance;"
        >
          La confianza que mereces, <span class="gradient-text">la calidad que necesitas</span>
        </h2>
      </div>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5">
        <div
          v-for="(feature, index) in features"
          :key="index"
          :class="[
            'group relative rounded-3xl overflow-hidden bento-item',
            feature.large ? 'sm:col-span-2 lg:col-span-1 min-h-80' : 'min-h-65',
            sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
          :style="{ transitionDelay: `${150 + index * 100}ms` }"
        >
          <template v-if="feature.image">
            <img
              :src="feature.image"
              :alt="feature.title"
              class="absolute inset-0 w-full h-full object-cover transition-transform duration-700 group-hover:scale-105"
              loading="lazy"
            >
            <div class="absolute inset-0 bg-linear-to-t from-clinic-dark/85 via-clinic-dark/30 to-transparent group-hover:from-clinic-primary/70 transition-all duration-500" />
          </template>
          <template v-else>
            <div class="absolute inset-0 bg-clinic-light group-hover:bg-clinic-primary/5 transition-colors duration-500" />
          </template>

          <div class="relative h-full flex flex-col justify-end p-7">
            <div
              :class="[
                'w-12 h-12 rounded-xl flex items-center justify-center mb-4 transition-all duration-300 group-hover:scale-110',
                feature.image
                  ? 'bg-white/10 backdrop-blur-sm border border-white/10'
                  : 'bg-clinic-primary/10'
              ]"
            >
              <UIcon
                :name="feature.icon"
                :class="[
                  'w-6 h-6',
                  feature.image ? 'text-clinic-secondary' : 'text-clinic-primary'
                ]"
              />
            </div>
            <h3
              :class="[
                'font-heading font-bold text-lg mb-2',
                feature.image ? 'text-white' : 'text-clinic-dark'
              ]"
            >
              {{ feature.title }}
            </h3>
            <p
              :class="[
                'text-sm leading-relaxed',
                feature.image ? 'text-white/60' : 'text-clinic-gray'
              ]"
            >
              {{ feature.description }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
