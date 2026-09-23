<script setup>
const parallaxY = ref(0)

const heroVisible = ref(false)

onMounted(() => {
  setTimeout(() => {
    heroVisible.value = true
  }, 100)

  window.addEventListener('scroll', () => {
    parallaxY.value = window.scrollY * 0.3
  }, { passive: true })
})
</script>

<template>
  <section
    id="inicio"
    class="relative min-h-screen flex items-center overflow-hidden"
  >
    <div
      class="absolute inset-0 w-full h-full"
      :style="{ transform: `translateY(${parallaxY}px)` }"
    >
      <img
        src="/img/FOTO 1.jpeg"
        alt="Clínica San Jorge"
        class="w-full h-full object-cover scale-110"
        loading="eager"
      >
    </div>

    <div class="absolute inset-0 hero-overlay" />

    <div class="absolute top-0 right-0 w-150 h-150 bg-clinic-secondary/10 rounded-full blur-[120px] pointer-events-none" />
    <div class="absolute bottom-0 left-0 w-100 h-100 bg-clinic-primary/10 rounded-full blur-[100px] pointer-events-none" />

    <div class="relative z-10 container mx-auto px-4 sm:px-6 lg:px-8 py-32 lg:py-0">
      <div class="max-w-3xl">
        <div
          :class="[
            'transition-all duration-1000 ease-out',
            heroVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
        >
        </div>

        <h1
          :class="[
            'font-heading text-4xl sm:text-5xl lg:text-7xl font-bold text-white leading-[1.1] mb-6 transition-all duration-1000 ease-out delay-150',
            heroVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
          style="text-wrap: balance;"
        >
          Tu salud es
          <span class="gradient-text-light">nuestra prioridad</span>
        </h1>

        <p
          :class="[
            'text-lg sm:text-xl text-white/70 leading-relaxed mb-10 max-w-xl transition-all duration-1000 ease-out delay-300',
            heroVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
        >
          Tecnología de vanguardia y un equipo humano comprometido con tu bienestar.
        </p>

        <div
          :class="[
            'flex flex-col sm:flex-row gap-4 mb-16 transition-all duration-1000 ease-out delay-450',
            heroVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
        >
          <UButton
            label="Solicitar Cita"
            icon="i-lucide-calendar"
            color="secondary"
            variant="solid"
            size="xl"
            class="shadow-lg shadow-clinic-secondary/30"
            to="#contacto"
          />
          <UButton
            label="Conocer Servicios"
            icon="i-lucide-arrow-right"
            color="white"
            variant="outline"
            size="xl"
            class="border-white/25 text-white hover:bg-white/10"
            to="#servicios"
          />
        </div>

      </div>
    </div>

    <!-- <div class="absolute bottom-8 left-1/2 -translate-x-1/2 z-10 animate-float">
      <div class="w-6 h-10 border-2 border-white/30 rounded-full flex justify-center pt-2">
        <div class="w-1.5 h-1.5 bg-white/60 rounded-full animate-bounce" />
      </div>
    </div> -->
  </section>
</template>
