<script setup>
const scenes = [
  {
    step: '01',
    title: 'Algo no está bien',
    description: 'Tu cuerpo te envía señales. No las ignores. En Clínica San Jorge te ayudamos a interpretarlas a tiempo.',
    service: 'Atención integral',
    serviceIcon: 'i-lucide-heart-pulse',
    image: '/img/FOTO 9.jpeg',
    overlay: 'from-clinic-dark/90 via-clinic-dark/50 to-clinic-dark/70',
    accent: 'bg-red-500/20 border-red-500/30 text-red-400',
    objective: 'Detectar a tiempo cualquier señal de alerta y dar el seguimiento correcto antes de que sea tarde.',
    services: [
      { icon: 'i-lucide-stethoscope', name: 'Medicina general', desc: 'Primera valoración con historia clínica y triage.' },
      { icon: 'i-lucide-flask-conical', name: 'Laboratorio clínico', desc: 'Análisis de I, II y III nivel con resultados oportunos.' },
      { icon: 'i-lucide-scan', name: 'Imágenes diagnósticas', desc: 'Estudios precisos con equipos de última generación.' }
    ],
    stats: [
      { value: '24/7', label: 'Disponibilidad' },
      { value: '6', label: 'Servicios integrales' }
    ],
    ctas: []
  },
  {
    step: '02',
    title: 'Un llamado de ayuda',
    description: 'Un solo paso te separa de la atención que necesitas. Contáctanos y recibe orientación inmediata.',
    service: 'Contacto inmediato',
    serviceIcon: 'i-lucide-phone',
    image: '/img/FOTO 38.jpeg',
    overlay: 'from-clinic-primary/80 via-clinic-primary/40 to-clinic-dark/60',
    accent: 'bg-clinic-primary/20 border-clinic-primary/30 text-clinic-accent',
    objective: 'Acortar la distancia entre tu necesidad y la atención médica, con canales de contacto directos y una admisión sin complicaciones.',
    services: [
      { icon: 'i-lucide-message-circle', name: 'Línea de atención', desc: 'Habla con nuestro equipo y recibe orientación para tu visita.' },
      { icon: 'i-lucide-calendar-check', name: 'Gestión de citas', desc: 'Agenda tu valoración y prepara tu visita con antelación.' },
      { icon: 'i-lucide-clipboard-check', name: 'Admisión ágil', desc: 'Trámites de ingreso claros y acompañamiento en cada paso.' }
    ],
    stats: [
      { value: '1', label: 'Paso para empezar' }
    ],
    ctas: [
      { label: 'Contactar ahora', icon: 'i-lucide-phone', href: 'tel:', variant: 'solid' }
    ]
  },
  {
    step: '03',
    title: 'En camino',
    description: 'Nuestro transporte asistencial llega donde nos necesites, con seguridad y acompañamiento profesional.',
    service: 'Transporte asistencial 24/7',
    serviceIcon: 'i-lucide-truck',
    image: '/img/FOTO 2.jpeg',
    overlay: 'from-clinic-dark/80 via-clinic-secondary/20 to-clinic-dark/60',
    accent: 'bg-clinic-secondary/20 border-clinic-secondary/30 text-clinic-secondary',
    objective: 'Trasladar al paciente con seguridad y acompañamiento profesional, esté donde esté, a cualquier hora del día.',
    services: [
      { icon: 'i-lucide-truck', name: 'Transporte básico', desc: 'Traslados seguros para citas, controles y exámenes.' },
      { icon: 'i-lucide-heart-pulse', name: 'Transporte medicalizado', desc: 'Paciente monitoreado por personal paramédico durante el traslado.' },
      { icon: 'i-lucide-clock-4', name: 'Flota 24/7', desc: 'Vehículos disponibles a cualquier hora, incluso fines de semana.' }
    ],
    stats: [
      { value: '24/7', label: 'Flota disponible' },
      { value: '2', label: 'Modalidades de traslado' }
    ],
    ctas: []
  },
  {
    step: '04',
    title: 'Bienvenido',
    description: 'Un espacio diseñado para que te sientas seguro y acompañado desde el primer momento.',
    service: 'Consulta externa',
    serviceIcon: 'i-lucide-stethoscope',
    image: '/img/FOTO 8.jpeg',
    overlay: 'from-clinic-dark/70 via-clinic-primary/30 to-clinic-dark/50',
    accent: 'bg-clinic-accent/20 border-clinic-accent/30 text-clinic-accent',
    objective: 'Recibir a cada paciente en un espacio seguro, humano y preparado para brindar tranquilidad desde la primera consulta.',
    services: [
      { icon: 'i-lucide-stethoscope', name: 'Consulta externa', desc: 'Valoración médica con privacidad, calidez y tiempo para ti.' },
      { icon: 'i-lucide-users', name: 'Equipo humano', desc: 'Profesionales que te acompañan en cada paso de tu atención.' },
      { icon: 'i-lucide-shield-check', name: 'Seguridad del paciente', desc: 'Protocolos rigurosos en cada procedimiento.' }
    ],
    stats: [
      { value: '4', label: 'Valores que nos guían' }
    ],
    ctas: [
      { label: 'Solicitar cita', icon: 'i-lucide-calendar', href: '#contacto', variant: 'solid' }
    ]
  },
  {
    step: '05',
    title: 'En buenas manos',
    description: 'Especialistas, tecnología y compromiso trabajando juntos por un diagnóstico preciso y un plan efectivo.',
    service: 'Laboratorio + Imágenes + Especialidades',
    serviceIcon: 'i-lucide-microscope',
    image: '/img/FOTO 31.jpeg',
    overlay: 'from-clinic-primary/70 via-clinic-primary/30 to-clinic-dark/50',
    accent: 'bg-clinic-secondary/20 border-clinic-secondary/30 text-clinic-secondary',
    objective: 'Brindar diagnósticos precisos y planes de tratamiento efectivos con tecnología de vanguardia y especialistas de alto nivel.',
    services: [
      { icon: 'i-lucide-flask-conical', name: 'Laboratorio clínico', desc: 'Análisis confiables para decisiones médicas seguras.' },
      { icon: 'i-lucide-scan', name: 'Imágenes diagnósticas', desc: 'Ecografías y estudios con equipos de última generación.' },
      { icon: 'i-lucide-heart-pulse', name: 'Especialidades médicas', desc: 'Cardiología, pediatría, neurología, gastroenterología y más.' }
    ],
    stats: [
      { value: '16', label: 'Especialidades' },
      { value: '3', label: 'Líneas diagnósticas' }
    ],
    ctas: []
  },
  {
    step: '06',
    title: 'De vuelta a casa',
    description: 'Tu recuperación continúa con atención personalizada en tu hogar y seguimiento constante.',
    service: 'Atención domiciliaria',
    serviceIcon: 'i-lucide-home',
    image: '/img/FOTO 7.jpeg',
    overlay: 'from-clinic-dark/60 via-clinic-secondary/20 to-clinic-dark/40',
    accent: 'bg-clinic-secondary/20 border-clinic-secondary/30 text-clinic-secondary',
    objective: 'Asegurar que la recuperación continúe con la misma calidad en el hogar, mediante cuidado personalizado y seguimiento oportuno.',
    services: [
      { icon: 'i-lucide-home', name: 'Atención domiciliaria', desc: 'Equipo profesional en tu hogar con plan de manejo.' },
      { icon: 'i-lucide-phone', name: 'Seguimiento', desc: 'Controles y orientación médica después de tu alta.' },
      { icon: 'i-lucide-calendar-check', name: 'Citas de control', desc: 'Revaloraciones para cuidar tu evolución.' }
    ],
    stats: [
      { value: '24/7', label: 'Transporte de apoyo' }
    ],
    ctas: [
      { label: 'Conocer servicios', icon: 'i-lucide-arrow-right', href: '#servicios', variant: 'solid' },
      { label: 'Solicitar cita', icon: 'i-lucide-calendar', href: '#contacto', variant: 'outline' }
    ]
  }
]

const activeScene = ref(0)
const scrollActivate = ref(true)
const progress = computed(() => activeScene.value / (scenes.length - 1))

let observer

onMounted(() => {
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (!entry.isIntersecting) return
        activeScene.value = Number(entry.target.id.replace('scene-', ''))
      })
    },
    {
      rootMargin: '-45% 0px -45% 0px',
      threshold: 0
    }
  )

  document
    .querySelectorAll('#narrativa [id^="scene-"]')
    .forEach(el => observer.observe(el))
  timeChange(0)

})

function handleUserInteraction() {
  if(activeScene.value < 2) return
  scrollActivate.value = false
}

onMounted(() => {
  window.addEventListener('wheel', handleUserInteraction, { passive: true })
  window.addEventListener('touchmove', handleUserInteraction, { passive: true })
})


onBeforeUnmount(() => {
  window.removeEventListener('wheel', handleUserInteraction)
  window.removeEventListener('touchmove', handleUserInteraction)
  observer?.disconnect()
})

function scrollToScene(accion) {
  const section = document.getElementById('narrativa')
  if (!section || (activeScene.value >= 5 && accion === 'mas')) return
  const sceneHeight = section.offsetHeight / (scenes.length + 1)
  const target = section.offsetTop + sceneHeight * (accion === 'mas' ? activeScene.value + 2 : activeScene.value)
  window.scrollTo({ top: target, behavior: 'smooth' })
}

watch(activeScene, (scene) => {
  timeChange(scene)
})

function timeChange (scene) {
  if (scene >= scenes.length - 1) return
  if (scene < 5 && scrollActivate.value) {
    setTimeout(() => scrollToScene('mas'), 5000)
  }
}
</script>

<template>
  <section
    id="narrativa"
    class="relative"
    :style="{ height: `${(scenes.length + 1) * 100}vh` }"
  >
    <div class="sticky top-0 h-screen overflow-hidden">
      <div class="absolute inset-0">
        <img
          v-for="(scene, index) in scenes"
          :key="scene.image"
          :src="scene.image"
          :alt="scene.title"
          :loading="index === 0 ? 'eager' : 'lazy'"
          :class="[
            'absolute inset-0 w-full h-full object-cover transition-all duration-1000 ease-out',
            index === activeScene ? 'opacity-100 scale-100' : 'opacity-0 scale-105'
          ]"
        >
        <div
          v-for="(scene, index) in scenes"
          :key="`overlay-${index}`"
          :class="[
            'absolute inset-0 bg-linear-to-r transition-opacity duration-700',
            scene.overlay,
            index === activeScene ? 'opacity-100' : 'opacity-0'
          ]"
        />
      </div>

      <!-- <NarrativeProgress
        :scenes="scenes"
        :active-scene="activeScene"
        :progress="progress"
      /> -->

      <div class="relative z-10 h-full flex items-center">
        <div class="container mx-auto px-4 sm:px-6 lg:px-8 w-full pt-16 pb-24 sm:pt-20 sm:pb-20">
          <Transition
            name="scene"
            mode="out-in"
          >
            <div
              :key="activeScene"
              class="grid lg:grid-cols-5 gap-7 lg:gap-12 items-center"
            >
              <div class="lg:col-span-3">
                <!-- <div
                  :class="[
                    'scene-anim inline-flex items-center gap-2 rounded-full px-4 py-1.5 mb-5 border',
                    scenes[activeScene].accent
                  ]"
                  style="animation-delay: 0ms"
                >
                  <UIcon
                    :name="scenes[activeScene].serviceIcon"
                    class="w-4 h-4"
                  />
                  <span class="text-sm font-medium">{{ scenes[activeScene].service }}</span>
                </div> -->

                <div class="flex items-baseline gap-4 mb-4">
                  <span
                    class="scene-anim hidden sm:block font-heading text-7xl lg:text-8xl font-bold text-white/20 leading-none select-none"
                    style="animation-delay: 60ms"
                  >
                    {{ scenes[activeScene].step }}
                  </span>
                </div>

                <h2
                  class="scene-anim font-heading text-3xl sm:text-4xl lg:text-5xl xl:text-6xl font-bold text-white leading-tight mb-4"
                  style="animation-delay: 120ms; text-wrap: balance;"
                >
                  {{ scenes[activeScene].title }}
                </h2>

                <p
                  class="scene-anim text-base sm:text-lg text-white/70 leading-relaxed mb-6 max-w-xl"
                  style="animation-delay: 180ms"
                >
                  {{ scenes[activeScene].description }}
                </p>

                <div
                  v-if="scenes[activeScene].ctas.length"
                  class="scene-anim flex flex-col sm:flex-row gap-3"
                  style="animation-delay: 240ms"
                >
                  <UButton
                    v-for="cta in scenes[activeScene].ctas"
                    :key="cta.label"
                    :label="cta.label"
                    :icon="cta.icon"
                    :href="cta.href"
                    :color="cta.variant === 'outline' ? 'white' : 'secondary'"
                    :variant="cta.variant"
                    size="lg"
                    :class="cta.variant === 'outline' ? 'border-white/25 text-white hover:bg-white/10' : ''"
                  />
                </div>
              </div>

              <div class="lg:col-span-2 w-full">
                <div
                  class="scene-anim glass-card-dark rounded-2xl p-5 sm:p-6 backdrop-blur-md"
                  style="animation-delay: 200ms"
                >
                  <div class="flex items-center gap-2 mb-3">
                    <div class="w-7 h-7 bg-clinic-secondary/15 border border-clinic-secondary/30 rounded-lg flex items-center justify-center shrink-0">
                      <UIcon
                        name="i-lucide-target"
                        class="w-4 h-4 text-clinic-secondary"
                      />
                    </div>
                    <span class="text-xs font-semibold tracking-wider uppercase text-clinic-secondary">
                      Nuestro objetivo
                    </span>
                  </div>

                  <p class="text-sm sm:text-[0.95rem] text-white/75 leading-relaxed mb-5">
                    {{ scenes[activeScene].objective }}
                  </p>

                  <div class="h-px bg-white/10 mb-5" />

                  <div class="flex items-center gap-2 mb-3">
                    <UIcon
                      name="i-lucide-layout-grid"
                      class="w-3.5 h-3.5 text-clinic-accent"
                    />
                    <span class="text-xs font-semibold tracking-wider uppercase text-clinic-accent">
                      Servicios en esta etapa
                    </span>
                  </div>

                  <ul class="space-y-3">
                    <li
                      v-for="svc in scenes[activeScene].services"
                      :key="svc.name"
                      class="flex items-start gap-3"
                    >
                      <span class="w-8 h-8 bg-white/8 border border-white/10 rounded-lg flex items-center justify-center shrink-0 mt-0.5">
                        <UIcon
                          :name="svc.icon"
                          class="w-4 h-4 text-clinic-accent"
                        />
                      </span>
                      <span class="min-w-0">
                        <span class="block text-sm font-semibold text-white leading-snug">
                          {{ svc.name }}
                        </span>
                        <span class="hidden sm:block text-xs text-white/50 leading-snug mt-0.5">
                          {{ svc.desc }}
                        </span>
                      </span>
                    </li>
                  </ul>

                  <!-- <div
                    v-if="scenes[activeScene].stats?.length"
                    class="flex flex-wrap gap-2 mt-5 pt-4 border-t border-white/10"
                  >
                    <span
                      v-for="stat in scenes[activeScene].stats"
                      :key="stat.label"
                      class="inline-flex items-baseline gap-1.5 bg-white/8 border border-white/10 rounded-full px-3 py-1.5"
                    >
                      <span class="font-heading font-bold text-clinic-secondary text-sm">
                        {{ stat.value }}
                      </span>
                      <span class="text-[0.7rem] text-white/50">
                        {{ stat.label }}
                      </span>
                    </span>
                  </div> -->
                </div>
              </div>
            </div>
          </Transition>
        </div>
      </div>

      <div class="absolute bottom-5 left-1/2 -translate-x-1/2 z-20 flex flex-col items-center gap-2">
        <div class="flex gap-3">
          <UButton icon="i-lucide-arrow-left" @click="scrollToScene('menos')" variant="soft"/>
          <div class="flex flex-col justify-center items-center">
            <span class="text-white/40 text-xs font-medium tracking-wider uppercase">
              Escena {{ activeScene + 1 }} / {{ scenes.length }}
            </span>
            <div class="flex gap-1.5">
              <div
                v-for="(_, index) in scenes"
                :key="index"
                :class="[
                  'h-1 rounded-full transition-all duration-500',
                  index === activeScene
                    ? 'w-8 bg-clinic-secondary'
                    : index < activeScene
                      ? 'w-2 bg-clinic-secondary/40'
                      : 'w-2 bg-white/15'
                ]"
              />
            </div>
          </div>
          <UButton icon="i-lucide-arrow-right" @click="scrollToScene('mas')" variant="soft"/>
        </div>
      </div>
    </div>

    <div
      v-for="(scene, index) in scenes"
      :id="`scene-${index}`"
      :key="`marker-${index}`"
      class="h-screen"
      aria-hidden="true"
    />
  </section>
</template>

<style scoped>
.scene-enter-active {
  transition: opacity 0.45s ease, transform 0.45s cubic-bezier(0.16, 1, 0.3, 1);
}

.scene-leave-active {
  transition: opacity 0.25s ease;
}

.scene-enter-from {
  opacity: 0;
  transform: translateY(24px);
}

.scene-leave-to {
  opacity: 0;
}

.scene-enter-active .scene-anim {
  animation: sceneIn 0.6s cubic-bezier(0.16, 1, 0.3, 1) both;
}

@keyframes sceneIn {
  from {
    opacity: 0;
    transform: translateY(18px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (prefers-reduced-motion: reduce) {
  .scene-enter-active,
  .scene-leave-active,
  .scene-enter-active .scene-anim {
    transition: none;
    animation: none;
  }
}
</style>
