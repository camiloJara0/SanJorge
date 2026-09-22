<script setup>
const services = [
  { icon: 'i-lucide-stethoscope', title: 'Consulta Externa', description: 'Valoración médica especializada para diagnóstico y tratamiento integral.', image: '/img/FOTO 2.jpeg' },
  { icon: 'i-lucide-flask-conical', title: 'Laboratorio Clínico', description: 'Análisis de laboratorio I, II y III nivel con tecnología de vanguardia.', image: '/img/FOTO 3.jpeg' },
  { icon: 'i-lucide-scan', title: 'Imágenes Diagnósticas', description: 'Estudios de imágenes precisos con equipos de última generación.', image: '/img/FOTO 4.jpeg' },
  { icon: 'i-lucide-truck', title: 'Transporte Asistencial', description: 'Transporte básico y medicalizado disponible las 24 horas.', image: '/img/FOTO 6.jpeg' },
  { icon: 'i-lucide-home', title: 'Atención Domiciliaria', description: 'Recuperación en casa con equipo profesional y plan de manejo.', image: '/img/FOTO 7.jpeg' },
  { icon: 'i-lucide-baby', title: 'Pediátrico', description: 'Atención integral para niños con especialistas certificados.', image: '/img/FOTO 8.jpeg' }
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
  const el = document.getElementById('servicios')
  if (el) observer.observe(el)
})
</script>

<template>
  <section
    id="servicios"
    class="py-28 lg:py-36 bg-clinic-light relative overflow-hidden"
  >
    <div class="absolute bottom-0 left-0 w-125 h-125 bg-clinic-accent/20 rounded-full blur-[120px] pointer-events-none" />

    <div class="container mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div
        :class="[
          'text-center mb-20 transition-all duration-800 ease-out',
          sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
        ]"
      >
        <!-- <div class="inline-flex items-center gap-2 bg-clinic-primary/5 rounded-full px-4 py-1.5 mb-6">
          <div class="w-1.5 h-1.5 bg-clinic-primary rounded-full" />
          <span class="text-clinic-primary text-sm font-semibold tracking-wide uppercase">Servicios</span>
        </div> -->
        <h2
          class="font-heading text-3xl sm:text-4xl lg:text-5xl font-bold text-clinic-dark mb-5"
          style="text-wrap: balance;"
        >
          Servicios médicos <span class="gradient-text">integrales</span>
        </h2>
        <p class="text-lg text-clinic-gray max-w-2xl mx-auto">
          Cuidamos tu salud con los más altos estándares de calidad y tecnología.
        </p>
      </div>

      <UCarousel
        :items="services"
        :autoplay="{ delay: 6000 }"
        :ui="{
          item: 'basis-full sm:basis-1/2 lg:basis-[45%]',
          container: 'gap-6'
        }"
        :class="[
          'transition-all duration-800 ease-out delay-200',
          sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'
        ]"
      >
        <template #default="{ item }">
          <div class="group relative rounded-3xl overflow-hidden h-105 sm:h-115 cursor-pointer">
            <img
              :src="item.image"
              :alt="item.title"
              class="absolute inset-0 w-full h-full object-cover transition-transform duration-700 group-hover:scale-110"
              loading="lazy"
            >
            <div class="absolute inset-0 bg-linear-to-t from-clinic-dark/80 via-clinic-dark/20 to-transparent" />
            <div class="absolute inset-0 bg-clinic-primary/0 group-hover:bg-clinic-primary/10 transition-all duration-500" />

            <div class="absolute top-5 left-5">
              <div class="w-12 h-12 bg-white/15 backdrop-blur-sm rounded-xl flex items-center justify-center border border-white/10">
                <UIcon
                  :name="item.icon"
                  class="w-6 h-6 text-white"
                />
              </div>
            </div>

            <div class="absolute bottom-0 left-0 right-0 p-7">
              <h3 class="font-heading font-bold text-white text-xl mb-2 group-hover:text-clinic-accent transition-colors">
                {{ item.title }}
              </h3>
              <p class="text-white/60 text-sm leading-relaxed mb-5 line-clamp-2">
                {{ item.description }}
              </p>
              <div class="flex items-center gap-2 text-clinic-secondary text-sm font-semibold opacity-0 translate-y-3 group-hover:opacity-100 group-hover:translate-y-0 transition-all duration-300">
                <span>Ver más</span>
                <UIcon
                  name="i-lucide-arrow-right"
                  class="w-4 h-4"
                />
              </div>
            </div>
          </div>
        </template>
      </UCarousel>
    </div>
  </section>
</template>
