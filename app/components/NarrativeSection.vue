<script setup>
const scenes = [
  {
    step: '01',
    title: 'Algo no está bien',
    description: 'Tu cuerpo te envía señales. No las ignores: la prevención y promoción de la salud nos permite actuar a tiempo.',
    service: 'Prevención y medicina general',
    serviceIcon: 'i-lucide-heart-pulse',
    image: '/img/FOTO 9.jpeg',
    overlay: 'from-clinic-dark/90 via-clinic-dark/50 to-clinic-dark/70',
    accent: 'bg-red-500/20 border-red-500/30 text-red-400',
    objective: 'Prevenir y promocionar la salud con intervenciones personalizadas que buscan mejorar la calidad de vida de quienes confían en nosotros.',
    services: [
      { icon: 'i-lucide-shield-check', name: 'Prevención y promoción', desc: 'Intervenciones personalizadas para cuidar tu bienestar integral.' },
      { icon: 'i-lucide-stethoscope', name: 'Consulta externa medicina general', desc: 'Primera valoración para detectar a tiempo cualquier señal.' },
      { icon: 'i-lucide-activity', name: 'Procedimientos diagnósticos y terapéuticos', desc: 'Procedimientos que apoyan el diagnóstico y el tratamiento.' }
    ],
    stats: [
      { value: 'Cali', label: 'Sede principal' },
      { value: '3', label: 'Servicios modelo' }
    ],
    ctas: []
  },
  {
    step: '02',
    title: 'Un llamado de ayuda',
    description: 'Un solo paso te separa de la atención que necesitas: acceso oportuno, tiempos de espera mínimos y trato cercano.',
    service: 'Atención inmediata',
    serviceIcon: 'i-lucide-zap',
    image: '/img/FOTO 38.jpeg',
    overlay: 'from-clinic-primary/80 via-clinic-primary/40 to-clinic-dark/60',
    accent: 'bg-clinic-primary/20 border-clinic-primary/30 text-clinic-accent',
    objective: 'Minimizar los tiempos de espera y facilitar el acceso a una atención cercana, segura y de alta calidad.',
    services: [
      { icon: 'i-lucide-stethoscope', name: 'Consulta externa medicina especializada', desc: 'Acceso a especialistas cuando tu caso lo requiere.' },
      { icon: 'i-lucide-hand-heart', name: 'Enfermería', desc: 'Acompañamiento profesional desde tu llegada.' },
      { icon: 'i-lucide-brain', name: 'Psicología', desc: 'Apoyo emocional integral durante tu atención.' }
    ],
    stats: [
      { value: '4', label: 'Principios corporativos' }
    ],
    ctas: [
      { label: 'Contactar ahora', icon: 'i-lucide-phone', href: 'tel:', variant: 'solid' }
    ]
  },
  {
    step: '03',
    title: 'En camino',
    description: 'Nuestro transporte asistencial básico y medicalizado llega donde nos necesites, con atención inmediata y seguridad en cada traslado.',
    service: 'Traslado asistencial',
    serviceIcon: 'i-lucide-truck',
    image: '/img/FOTO 2.jpeg',
    overlay: 'from-clinic-dark/80 via-clinic-secondary/20 to-clinic-dark/60',
    accent: 'bg-clinic-secondary/20 border-clinic-secondary/30 text-clinic-secondary',
    objective: 'Trasladar al paciente de forma segura, con transporte básico o medicalizado y atención inmediata cuando se necesita.',
    services: [
      { icon: 'i-lucide-truck', name: 'Transporte asistencial básico', desc: 'Traslado terrestre primario y secundario para tus citas.' },
      { icon: 'i-lucide-heart-pulse', name: 'Transporte asistencial medicalizado', desc: 'Soporte de personal de salud durante todo el recorrido.' },
      { icon: 'i-lucide-clock-4', name: 'Atención inmediata', desc: 'Respuesta ágil cuando necesitas un traslado.' }
    ],
    stats: [
      { value: '4', label: 'Modalidades de traslado' },
      { value: '2', label: 'Básico y medicalizado' }
    ],
    ctas: []
  },
  {
    step: '04',
    title: 'Bienvenido',
    description: 'Un espacio diseñado para que te sientas seguro desde el primer momento, con trato cálido, profesional y humanizado.',
    service: 'Consulta externa y especialidades',
    serviceIcon: 'i-lucide-stethoscope',
    image: '/img/FOTO 8.jpeg',
    overlay: 'from-clinic-dark/70 via-clinic-primary/30 to-clinic-dark/50',
    accent: 'bg-clinic-accent/20 border-clinic-accent/30 text-clinic-accent',
    objective: 'Recibir a cada paciente con trato cálido y profesional, bajo los principios de eficiencia, humanización, seguridad y transparencia.',
    services: [
      { icon: 'i-lucide-users', name: 'Medicina especializada', desc: '17 especialidades: pediatría, cardiología, neurología y más.' },
      { icon: 'i-lucide-baby', name: 'Pediátrico', desc: 'Pediatría, cardiología y neurología pediátrica.' },
      { icon: 'i-lucide-utensils', name: 'Nutrición', desc: 'Orientación nutricional complementaria a tu tratamiento.' }
    ],
    stats: [
      { value: '17', label: 'Especialidades' },
      { value: '4', label: 'Compromisos de calidad' }
    ],
    ctas: [
      { label: 'Solicitar cita', icon: 'i-lucide-calendar', href: '#contacto', variant: 'solid' }
    ]
  },
  {
    step: '05',
    title: 'En buenas manos',
    description: 'Especialistas, tecnología y altos estándares: laboratorio e imagenología de I, II y III nivel para un diagnóstico preciso.',
    service: 'Laboratorio e imagenología',
    serviceIcon: 'i-lucide-microscope',
    image: '/img/FOTO 31.jpeg',
    overlay: 'from-clinic-primary/70 via-clinic-primary/30 to-clinic-dark/50',
    accent: 'bg-clinic-secondary/20 border-clinic-secondary/30 text-clinic-secondary',
    objective: 'Brindar diagnósticos precisos en laboratorio e imágenes de I, II y III nivel, dentro de un marco de seguridad y confianza.',
    services: [
      { icon: 'i-lucide-flask-conical', name: 'Laboratorio clínico', desc: 'Toma de muestras y laboratorio de I, II y III nivel.' },
      { icon: 'i-lucide-scan', name: 'Imagenología', desc: 'Estudios de imágenes de I, II y III nivel.' },
      { icon: 'i-lucide-monitor', name: 'Imágenes no ionizantes', desc: 'Estudios seguros con tecnología de precisión.' }
    ],
    stats: [
      { value: 'I, II y III', label: 'Lab. e imágenes' }
    ],
    ctas: []
  },
  {
    step: '06',
    title: 'De vuelta a casa',
    description: 'Tu hogar es el lugar ideal para tu recuperación: cuidamos tu bienestar con un plan de manejo ambulatorio complementario.',
    service: 'Atención domiciliaria',
    serviceIcon: 'i-lucide-home',
    image: '/img/FOTO 7.jpeg',
    overlay: 'from-clinic-dark/60 via-clinic-secondary/20 to-clinic-dark/40',
    accent: 'bg-clinic-secondary/20 border-clinic-secondary/30 text-clinic-secondary',
    objective: 'Respaldar tu bienestar en casa con un plan de manejo ambulatorio complementario y un equipo que acompaña a tu familia en cada paso.',
    services: [
      { icon: 'i-lucide-home', name: 'Atención domiciliaria Home-Care', desc: 'Profesionales humanizados en tu hogar, en cada paso del proceso.' },
      { icon: 'i-lucide-bed', name: 'Hospitalización domiciliaria', desc: 'Pacientes crónicos, con y sin ventilador.' },
      { icon: 'i-lucide-heart-handshake', name: 'Dolor y cuidados paliativos', desc: 'Alivio y acompañamiento con foco en tu calidad de vida.' }
    ],
    stats: [
      { value: '2028', label: 'Meta de acreditación' }
    ],
    ctas: [
      { label: 'Conocer servicios', icon: 'i-lucide-arrow-right', href: '#servicios', variant: 'solid' },
      { label: 'Solicitar cita', icon: 'i-lucide-calendar', href: '#contacto', variant: 'outline' }
    ]
  }
]

const AUTO_PLAY_DELAY = 5000
const WHEEL_GESTURE_GAP = 250
const INPUT_SETTLE_MS = 500
const NAV_KEYS = new Set(['ArrowUp', 'ArrowDown', 'PageUp', 'PageDown', 'Home', 'End', ' ', 'Spacebar'])

const activeScene = ref(0)
const autoPlay = ref(true)
const sectionInView = ref(false)
const progress = computed(() => activeScene.value / (scenes.length - 1))

let sceneObserver
let autoTimer = null
let programmatic = false
let programmaticFallback = null
let lastWheelAt = 0
let lastInputAt = 0
let wheelGestureNavigating = false

function cancelAutoPlay() {
  autoPlay.value = false
  clearTimeout(autoTimer)
  autoTimer = null
}

function scheduleAutoPlay() {
  clearTimeout(autoTimer)
  autoTimer = null

  if (!autoPlay.value || !sectionInView.value) return

  if (activeScene.value >= scenes.length - 1) {
    autoPlay.value = false
    return
  }

  autoTimer = setTimeout(() => {
    autoTimer = null
    if (!autoPlay.value || !sectionInView.value) return
    if (programmatic || Date.now() - lastInputAt < INPUT_SETTLE_MS) {
      scheduleAutoPlay()
      return
    }
    goToScene(activeScene.value + 1)
  }, AUTO_PLAY_DELAY)
}

function toggleAutoPlay() {
  if (autoPlay.value) {
    cancelAutoPlay()
    return
  }

  autoPlay.value = true

  if (activeScene.value >= scenes.length - 1) {
    goToScene(0)
    return
  }

  scheduleAutoPlay()
}

function endProgrammaticScroll() {
  programmatic = false
  clearTimeout(programmaticFallback)
  programmaticFallback = null
}

function goToScene(index) {
  const marker = document.getElementById(`scene-${index}`)
  if (!marker) return

  clearTimeout(autoTimer)
  autoTimer = null

  const top = marker.getBoundingClientRect().top + window.scrollY
  const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches
  const distance = Math.abs(top - window.scrollY)
  const estimate = prefersReducedMotion
    ? 100
    : Math.min(5000, 500 + (distance / Math.max(window.innerHeight, 1)) * 500)

  programmatic = true
  clearTimeout(programmaticFallback)
  programmaticFallback = setTimeout(endProgrammaticScroll, estimate + 1500)

  window.scrollTo({
    top,
    behavior: prefersReducedMotion ? 'auto' : 'smooth'
  })
}

function updateSectionInView() {
  const section = document.getElementById('narrativa')
  if (!section) return

  const rect = section.getBoundingClientRect()
  sectionInView.value = rect.top <= 2 && rect.bottom >= window.innerHeight - 2
}

function handleScroll() {
  updateSectionInView()
}

function handleScrollEnd() {
  if (programmatic) endProgrammaticScroll()
}

function handleWheel() {
  const now = Date.now()
  if (now - lastWheelAt > WHEEL_GESTURE_GAP) {
    wheelGestureNavigating = !sectionInView.value
  }
  lastWheelAt = now
  lastInputAt = now

  if (wheelGestureNavigating) return
  if (sectionInView.value) cancelAutoPlay()
}

function handleTouchstart(event) {
  lastInputAt = Date.now()
  if (event.target?.closest?.('button, a')) return
  if (sectionInView.value) cancelAutoPlay()
}

function handleKeydown(event) {
  if (event.target?.closest?.('input, textarea, select, [contenteditable], button, a')) return
  if (!NAV_KEYS.has(event.key)) return
  lastInputAt = Date.now()
  if (sectionInView.value) cancelAutoPlay()
}

function handleVisibilityChange() {
  if (document.hidden) {
    clearTimeout(autoTimer)
    autoTimer = null
    return
  }
  if (sectionInView.value) scheduleAutoPlay()
}

watch(activeScene, () => {
  if (autoPlay.value) scheduleAutoPlay()
})

watch(sectionInView, (visible) => {
  if (visible) {
    scheduleAutoPlay()
    return
  }
  clearTimeout(autoTimer)
  autoTimer = null
})

onMounted(() => {
  sceneObserver = new IntersectionObserver(
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
    .forEach(el => sceneObserver.observe(el))

  window.addEventListener('scroll', handleScroll, { passive: true })
  window.addEventListener('scrollend', handleScrollEnd, { passive: true })
  window.addEventListener('wheel', handleWheel, { passive: true, capture: true })
  window.addEventListener('touchstart', handleTouchstart, { passive: true, capture: true })
  window.addEventListener('keydown', handleKeydown, { passive: true })
  document.addEventListener('visibilitychange', handleVisibilityChange)

  updateSectionInView()
  if (sectionInView.value) scheduleAutoPlay()
})

onBeforeUnmount(() => {
  sceneObserver?.disconnect()
  clearTimeout(autoTimer)
  clearTimeout(programmaticFallback)
  window.removeEventListener('scroll', handleScroll)
  window.removeEventListener('scrollend', handleScrollEnd)
  window.removeEventListener('wheel', handleWheel, { capture: true })
  window.removeEventListener('touchstart', handleTouchstart, { capture: true })
  window.removeEventListener('keydown', handleKeydown)
  document.removeEventListener('visibilitychange', handleVisibilityChange)
})
</script>

<template>
  <section
    id="narrativa"
    class="relative"
    :style="{ height: `${scenes.length * 100}vh` }"
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
        @navigate="goToScene"
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
        <div class="flex items-center gap-3">
          <button
            type="button"
            class="w-8 h-8 rounded-full border border-white/20 bg-white/10 hover:bg-white/20 text-white/80 hover:text-white flex items-center justify-center transition-all duration-300 hover:scale-110 focus:outline-none focus-visible:ring-2 focus-visible:ring-clinic-secondary"
            :aria-label="autoPlay ? 'Pausar recorrido automático' : 'Reproducir recorrido automático'"
            @click="toggleAutoPlay"
          >
            <UIcon
              :name="autoPlay ? 'i-lucide-pause' : 'i-lucide-play'"
              class="w-3.5 h-3.5"
            />
          </button>
          <span class="text-white/40 text-xs font-medium tracking-wider uppercase">
            Escena {{ activeScene + 1 }} / {{ scenes.length }}
          </span>
          <div
            v-if="autoPlay && sectionInView"
            class="h-0.5 w-12 rounded-full bg-white/10 overflow-hidden"
          >
            <div
              :key="`auto-${activeScene}`"
              class="h-full bg-clinic-secondary rounded-full auto-advance"
              :style="{ animationDuration: `${AUTO_PLAY_DELAY}ms` }"
            />
          </div>
        </div>
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
    </div>

    <div
      v-for="(scene, index) in scenes"
      :id="`scene-${index}`"
      :key="`marker-${index}`"
      class="absolute left-0 w-full h-screen pointer-events-none"
      :style="{ top: `${index * 100}vh` }"
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

.auto-advance {
  animation-name: autoAdvance;
  animation-timing-function: linear;
  animation-fill-mode: both;
}

@keyframes autoAdvance {
  from {
    width: 0%;
  }
  to {
    width: 100%;
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
