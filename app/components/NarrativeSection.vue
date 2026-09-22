<script setup>
const scenes = [
  {
    step: '01',
    title: 'Algo no está bien',
    description: 'Tu cuerpo te envía señales. No las ignores.',
    service: 'Atención integral',
    serviceIcon: 'i-lucide-heart-pulse',
    image: '/img/FOTO 9.jpeg',
    overlay: 'from-clinic-dark/90 via-clinic-dark/50 to-clinic-dark/70',
    accent: 'bg-red-500/20 border-red-500/30 text-red-400'
  },
  {
    step: '02',
    title: 'Un llamado de ayuda',
    description: 'Un solo paso te separa de la atención que necesitas.',
    service: 'Contacto inmediato',
    serviceIcon: 'i-lucide-phone',
    image: '/img/FOTO 38.jpeg',
    overlay: 'from-clinic-primary/80 via-clinic-primary/40 to-clinic-dark/60',
    accent: 'bg-clinic-primary/20 border-clinic-primary/30 text-clinic-accent'
  },
  {
    step: '03',
    title: 'En camino',
    description: 'Nuestro transporte asistencial llega donde nos necesites.',
    service: 'Transporte asistencial 24/7',
    serviceIcon: 'i-lucide-truck',
    image: '/img/FOTO 2.jpeg',
    overlay: 'from-clinic-dark/80 via-clinic-secondary/20 to-clinic-dark/60',
    accent: 'bg-clinic-secondary/20 border-clinic-secondary/30 text-clinic-secondary'
  },
  {
    step: '04',
    title: 'Bienvenido',
    description: 'Un espacio diseñado para que te sientas seguro desde el primer momento.',
    service: 'Consulta externa',
    serviceIcon: 'i-lucide-stethoscope',
    image: '/img/FOTO 8.jpeg',
    overlay: 'from-clinic-dark/70 via-clinic-primary/30 to-clinic-dark/50',
    accent: 'bg-clinic-accent/20 border-clinic-accent/30 text-clinic-accent'
  },
  {
    step: '05',
    title: 'En buenas manos',
    description: 'Especialistas, tecnología y compromiso trabajando por ti.',
    service: 'Laboratorio + Imágenes + Especialidades',
    serviceIcon: 'i-lucide-microscope',
    image: '/img/FOTO 31.jpeg',
    overlay: 'from-clinic-primary/70 via-clinic-primary/30 to-clinic-dark/50',
    accent: 'bg-clinic-secondary/20 border-clinic-secondary/30 text-clinic-secondary'
  },
  {
    step: '06',
    title: 'De vuelta a casa',
    description: 'Tu recuperación continúa con atención personalizada en tu hogar.',
    service: 'Atención domiciliaria',
    serviceIcon: 'i-lucide-home',
    image: '/img/FOTO 7.jpeg',
    overlay: 'from-clinic-dark/60 via-clinic-secondary/20 to-clinic-dark/40',
    accent: 'bg-clinic-secondary/20 border-clinic-secondary/30 text-clinic-secondary'
  }
]

const activeScene = ref(0)

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (!entry.isIntersecting) return

        const id = entry.target.id
        const index = Number(id.replace('scene-', ''))

        activeScene.value = index

        console.log('Escena:', index)
      })
    },
    {
      threshold: 0.5
    }
  )

  document
    .querySelectorAll('[id^="scene-"]')
    .forEach(el => observer.observe(el))
})
</script>

<template>
  <section id="narrativa" class="relative" :style="{ height: `${scenes.length * 100}vh` }">
    <div class="sticky top-0 h-screen overflow-hidden">
      <NarrativeProgress :scenes="scenes" :active-scene="activeScene" />
      <div class="relative h-full w-full">
        <img :src="scenes[activeScene].image" :alt="scenes[activeScene].title"
          class="w-full h-full object-cover transition-transform duration-2000 ease-out" loading="lazy">
        <div :class="['absolute inset-0 bg-linear-to-r', scenes[activeScene].overlay]" />
      </div>
    </div>
    <div v-for="(scene, index) in scenes" :key="index" class="h-screen" :id="`scene-${index}`">
      <div class="absolute inset-0 flex items-center">
        <div class="container mx-auto px-4 sm:px-6 lg:px-8">
          <div class="max-w-2xl">
            <div :class="[
              'inline-flex items-center gap-2 rounded-full px-4 py-1.5 mb-6 border transition-all duration-700',
              scene.accent,
              index === activeScene
                ? 'opacity-100 translate-y-0'
                : 'opacity-0 translate-y-4'
            ]">
              <UIcon :name="scene.serviceIcon" class="w-4 h-4" />
              <span class="text-sm font-medium">{{ scene.service }}</span>
            </div>

            <div :class="[
              'flex items-baseline gap-4 mb-4 transition-all duration-700 delay-100',
              index === activeScene
                ? 'opacity-100 translate-y-0'
                : 'opacity-0 translate-y-6'
            ]">
              <span class="font-heading text-8xl sm:text-9xl font-bold text-white/5 leading-none select-none">
                {{ scene.step }}
              </span>
            </div>

            <h2 :class="[
              'font-heading text-4xl sm:text-5xl lg:text-6xl font-bold text-white leading-tight mb-5 transition-all duration-700 delay-200',
              index === activeScene
                ? 'opacity-100 translate-y-0'
                : 'opacity-0 translate-y-6'
            ]" style="text-wrap: balance;">
              {{ scene.title }}
            </h2>

            <p :class="[
              'text-lg sm:text-xl text-white/60 leading-relaxed mb-8 max-w-lg transition-all duration-700 delay-300',
              index === activeScene
                ? 'opacity-100 translate-y-0'
                : 'opacity-0 translate-y-6'
            ]">
              {{ scene.description }}
            </p>

            <div v-if="index === 5" :class="[
              'flex flex-col sm:flex-row gap-4 transition-all duration-700 delay-400',
              index === activeScene
                ? 'opacity-100 translate-y-0'
                : 'opacity-0 translate-y-6'
            ]">
              <UButton label="Conocer servicios" icon="i-lucide-arrow-right" color="secondary" variant="solid"
                size="lg" />
              <UButton label="Solicitar cita" icon="i-lucide-calendar" color="white" variant="outline" size="lg"
                class="border-white/25 text-white hover:bg-white/10" />
            </div>

            <div v-else-if="index === 1" :class="[
              'flex flex-col sm:flex-row gap-4 transition-all duration-700 delay-400',
              index === activeScene
                ? 'opacity-100 translate-y-0'
                : 'opacity-0 translate-y-6'
            ]">
              <UButton label="Contactar ahora" icon="i-lucide-phone" color="secondary" variant="solid" size="lg" />
            </div>
          </div>
        </div>
      </div>

      <div v-if="index === activeScene" class="absolute bottom-0 left-0 right-0 h-px">
        <div
          class="h-full bg-linear-to-r from-transparent via-clinic-secondary to-transparent transition-all duration-300" />
      </div>
    </div>

    <div class="absolute bottom-8 left-1/2 -translate-x-1/2 z-20 flex flex-col items-center gap-2">
      <span class="text-white/40 text-xs font-medium tracking-wider uppercase">
        Escena {{ activeScene + 1 }} / {{ scenes.length }}
      </span>
      <div class="flex gap-1.5">
        <div v-for="(_, index) in scenes" :key="index" :class="[
          'h-1 rounded-full transition-all duration-500',
          index === activeScene
            ? 'w-8 bg-clinic-secondary'
            : index < activeScene
              ? 'w-2 bg-clinic-secondary/40'
              : 'w-2 bg-white/15'
        ]" />
      </div>
    </div>
  </section>
</template>
