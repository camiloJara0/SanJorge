<script setup>
const testimonials = [
  {
    name: 'María Fernández',
    role: 'Paciente',
    text: 'Excelente atención. El personal médico es muy profesional y el trato es muy humano. Me sentí acompañada en todo momento.',
    rating: 5,
    avatar: '/img/FOTO 25.jpeg',
    large: true
  },
  {
    name: 'Carlos Rodríguez',
    role: 'Familiar de paciente',
    text: 'Atención excepcional cuando mi madre necesitó hospitalización domiciliaria. Equipo realmente comprometido.',
    rating: 5,
    avatar: '/img/FOTO 26.jpeg',
    large: false
  },
  {
    name: 'Ana Gutiérrez',
    role: 'Madre de paciente',
    text: 'Llevo a mis hijos al pediatría y siempre salen contentos. Doctores patientes y claros. Totalmente recomendados.',
    rating: 5,
    avatar: '/img/FOTO 27.jpeg',
    large: false
  }
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
    { threshold: 0.1 }
  )
  const el = document.getElementById('testimonios')
  if (el) observer.observe(el)
})
</script>

<template>
  <section
    id="testimonios"
    class="py-28 lg:py-36 relative overflow-hidden"
  >
    <div class="absolute bottom-0 left-0 w-125 h-125 bg-clinic-accent/15 rounded-full blur-[120px] pointer-events-none" />

    <div class="container mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div
        :class="[
          'text-center mb-20 transition-all duration-800 ease-out',
          sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
        ]"
      >
        <div class="inline-flex items-center gap-2 bg-clinic-primary/5 rounded-full px-4 py-1.5 mb-6">
          <div class="w-1.5 h-1.5 bg-clinic-primary rounded-full" />
          <span class="text-clinic-primary text-sm font-semibold tracking-wide uppercase">Testimonios</span>
        </div>
        <h2 class="font-heading text-3xl sm:text-4xl lg:text-5xl font-bold text-clinic-dark mb-5">
          Lo que dicen nuestros <span class="gradient-text">pacientes</span>
        </h2>
      </div>

      <div class="grid lg:grid-cols-3 gap-6 items-start">
        <div
          :class="[
            'lg:row-span-2 transition-all duration-800 ease-out',
            sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'
          ]"
          :style="{ transitionDelay: '150ms' }"
        >
          <div class="testimonial-card bg-clinic-white rounded-3xl p-8 sm:p-10 border border-clinic-muted/30 shadow-lg shadow-clinic-primary/5 h-full">
            <div class="text-6xl text-clinic-primary/15 font-heading font-bold leading-none mb-4">
              "
            </div>
            <p class="text-clinic-dark text-lg sm:text-xl leading-relaxed mb-8 font-medium">
              {{ testimonials[0].text }}
            </p>
            <div class="flex items-center gap-1 mb-6">
              <UIcon
                v-for="s in 5"
                :key="s"
                name="i-lucide-star"
                class="w-5 h-5 text-yellow-400"
              />
            </div>
            <div class="flex items-center gap-4 pt-6 border-t border-clinic-muted/30">
              <div class="w-14 h-14 rounded-2xl overflow-hidden bg-clinic-accent shrink-0">
                <img
                  :src="testimonials[0].avatar"
                  :alt="testimonials[0].name"
                  class="img-cover"
                  loading="lazy"
                >
              </div>
              <div>
                <div class="font-heading font-bold text-clinic-dark">
                  {{ testimonials[0].name }}
                </div>
                <div class="text-clinic-gray text-sm">
                  {{ testimonials[0].role }}
                </div>
              </div>
            </div>
          </div>
        </div>

        <div
          v-for="(t, i) in testimonials.slice(1)"
          :key="i"
          :class="[
            'transition-all duration-800 ease-out',
            sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'
          ]"
          :style="{ transitionDelay: `${300 + i * 150}ms` }"
        >
          <div class="testimonial-card bg-clinic-white rounded-3xl p-7 sm:p-8 border border-clinic-muted/30 shadow-md">
            <div class="flex items-center gap-1 mb-4">
              <UIcon
                v-for="s in 5"
                :key="s"
                name="i-lucide-star"
                class="w-4 h-4 text-yellow-400"
              />
            </div>
            <p class="text-clinic-dark leading-relaxed mb-6">
              "{{ t.text }}"
            </p>
            <div class="flex items-center gap-3 pt-5 border-t border-clinic-muted/30">
              <div class="w-11 h-11 rounded-xl overflow-hidden bg-clinic-accent shrink-0">
                <img
                  :src="t.avatar"
                  :alt="t.name"
                  class="img-cover"
                  loading="lazy"
                >
              </div>
              <div>
                <div class="font-heading font-semibold text-clinic-dark text-sm">
                  {{ t.name }}
                </div>
                <div class="text-clinic-gray text-xs">
                  {{ t.role }}
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
