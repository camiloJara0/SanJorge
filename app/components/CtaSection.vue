<script setup>
const parallaxY = ref(0)

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
    { threshold: 0.15 }
  )
  const el = document.getElementById('cta')
  if (el) observer.observe(el)

  window.addEventListener('scroll', () => {
    const rect = document.getElementById('cta')?.getBoundingClientRect()
    if (rect) {
      parallaxY.value = (window.innerHeight - rect.top) * 0.15
    }
  }, { passive: true })
})
</script>

<template>
  <section
    id="cta"
    class="relative overflow-hidden cta-glow"
  >
    <div
      class="absolute inset-0"
      :style="{ transform: `translateY(${parallaxY * 0.3}px)` }"
    >
      <img
        src="/img/FOTO 13.jpeg"
        alt=""
        class="w-full h-full object-cover scale-110"
        loading="lazy"
      >
      <div class="absolute inset-0 hero-overlay-dark" />
    </div>

    <div class="absolute inset-0 bg-clinic-primary/30" />

    <div class="relative z-10 py-32 lg:py-40">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div
          :class="[
            'max-w-3xl mx-auto text-center transition-all duration-1000 ease-out',
            sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'
          ]"
        >
          <div
            :class="[
              'inline-flex items-center gap-2 bg-white/10 backdrop-blur-sm rounded-full px-5 py-2 mb-8 border border-white/10 transition-all duration-700 delay-100',
              sectionVisible ? 'opacity-100 scale-100' : 'opacity-0 scale-90'
            ]"
          >
            <UIcon
              name="i-lucide-phone"
              class="w-4 h-4 text-clinic-secondary"
            />
            <span class="text-white/90 text-sm font-medium">Atención inmediata</span>
          </div>

          <h2
            :class="[
              'font-heading text-3xl sm:text-4xl lg:text-5xl font-bold text-white mb-6 transition-all duration-1000 delay-200',
              sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
            ]"
            style="text-wrap: balance;"
          >
            ¿Necesitas atención médica?
          </h2>

          <p
            :class="[
              'text-xl text-white/70 mb-10 max-w-xl mx-auto transition-all duration-1000 delay-300',
              sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
            ]"
          >
            Agenda tu cita hoy. Nuestro equipo está listo para cuidar de ti.
          </p>

          <div
            :class="[
              'flex flex-col sm:flex-row gap-4 justify-center mb-16 transition-all duration-1000 delay-400',
              sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
            ]"
          >
            <UButton
              label="Solicitar Cita Ahora"
              icon="i-lucide-calendar-check"
              color="secondary"
              variant="solid"
              size="xl"
              class="shadow-lg shadow-clinic-secondary/30"
              @click="document.querySelector('#contacto')?.scrollIntoView({ behavior: 'smooth' })"
            />
            <UButton
              label="Llamar Ahora"
              icon="i-lucide-phone"
              color="white"
              variant="outline"
              size="xl"
              class="border-white/25 text-white hover:bg-white/10"
              to="tel:"
            />
          </div>

          <div
            :class="[
              'grid grid-cols-3 gap-6 sm:gap-8 transition-all duration-1000 delay-500',
              sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
            ]"
          >
            <div class="glass-card rounded-2xl px-4 py-5 text-center">
              <div class="font-heading font-bold text-white text-2xl sm:text-3xl">
                15+
              </div>
              <div class="text-white/50 text-xs sm:text-sm mt-1">
                Años de experiencia
              </div>
            </div>
            <div class="glass-card rounded-2xl px-4 py-5 text-center">
              <div class="font-heading font-bold text-white text-2xl sm:text-3xl">
                24/7
              </div>
              <div class="text-white/50 text-xs sm:text-sm mt-1">
                Transporte asistencial
              </div>
            </div>
            <div class="glass-card rounded-2xl px-4 py-5 text-center">
              <div class="font-heading font-bold text-white text-2xl sm:text-3xl">
                20+
              </div>
              <div class="text-white/50 text-xs sm:text-sm mt-1">
                Especialidades
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
