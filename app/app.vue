<script setup>
const siteTitle = 'Clínica San Jorge | Atención Médica Integral en Cali'
const siteDescription = 'Clínica San Jorge - Atención médica especializada en Cali. Consulta externa, transporte asistencial, laboratorio e imágenes diagnósticas. Tu salud es nuestra prioridad.'

useHead({
  title: siteTitle,
  meta: [
    { name: 'viewport', content: 'width=device-width, initial-scale=1' },
    { name: 'description', content: siteDescription },
    { name: 'theme-color', content: '#004AAC' },
    { property: 'og:title', content: siteTitle },
    { property: 'og:description', content: siteDescription },
    { property: 'og:type', content: 'website' },
    { property: 'og:locale', content: 'es_CO' },
    { name: 'twitter:card', content: 'summary_large_image' },
    { name: 'twitter:title', content: siteTitle },
    { name: 'twitter:description', content: siteDescription }
  ],
  link: [
    { rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' },
    { rel: 'preconnect', href: 'https://fonts.gstatic.com', crossorigin: '' }
  ],
  htmlAttrs: { lang: 'es' },
  script: [
    {
      type: 'application/ld+json',
      innerHTML: JSON.stringify({
        '@context': 'https://schema.org',
        '@type': 'MedicalClinic',
        'name': 'Clínica San Jorge',
        'description': 'Institución de salud especializada en atención médica integral en Cali, Colombia.',
        'url': '#',
        'telephone': '+57-XXX-XXX-XXXX',
        'address': { '@type': 'PostalAddress', 'addressLocality': 'Cali', 'addressRegion': 'Valle del Cauca', 'addressCountry': 'CO' },
        'medicalSpecialty': ['Medicina General', 'Pediatría', 'Cardiología', 'Neurología', 'Gastroenterología', 'Dermatología'],
        'availableService': ['Consulta Externa', 'Laboratorio Clínico', 'Imágenes Diagnósticas', 'Transporte Asistencial', 'Atención Domiciliaria']
      })
    }
  ]
})

const navItems = [
  { label: 'Inicio', to: '#inicio' },
  { label: 'Nosotros', to: '#nosotros' },
  { label: 'Servicios', to: '#servicios' },
  { label: 'Especialidades', to: '#especialidades' },
  { label: 'Instalaciones', to: '#instalaciones' },
  { label: 'Contacto', to: '#contacto' }
]

const mobileMenuOpen = ref(false)
const scrolled = ref(false)

function scrollToSection(to) {
  mobileMenuOpen.value = false
  const el = document.querySelector(to)
  if (el) el.scrollIntoView({ behavior: 'smooth' })
}

onMounted(() => {
  window.addEventListener('scroll', () => {
    scrolled.value = window.scrollY > 60
  }, { passive: true })
})
</script>

<template>
  <UApp>
    <UHeader
      :class="[
        'fixed top-0 left-0 right-0 z-50 transition-all duration-500 border-b',
        scrolled
          ? 'bg-clinic-white/80 backdrop-blur-xl border-clinic-muted/30 shadow-sm'
          : 'bg-transparent border-transparent'
      ]"
    >
      <template #left>
        <NuxtLink
          to="#inicio"
          class="flex items-center gap-2.5"
          @click.prevent="scrollToSection('#inicio')"
        >
          <div class="w-10 h-10 bg-clinic-primary rounded-xl flex items-center justify-center shadow-md shadow-clinic-primary/20">
            <span class="text-white font-heading font-bold text-lg">SJ</span>
          </div>
          <div class="hidden sm:block">
            <span
              :class="[
                'font-heading font-bold text-lg leading-tight block transition-colors duration-500',
                scrolled ? 'text-clinic-primary' : 'text-white'
              ]"
            >Clínica</span>
            <span
              :class="[
                'font-heading font-semibold text-xs leading-tight block transition-colors duration-500',
                scrolled ? 'text-clinic-dark' : 'text-white/70'
              ]"
            >San Jorge</span>
          </div>
        </NuxtLink>
      </template>

      <UNavigationMenu
        :items="navItems.map(item => ({
          ...item,
          onClick: (e) => { e.preventDefault(); scrollToSection(item.to) }
        }))"
        :class="[
          'hidden lg:flex transition-colors duration-500',
          scrolled ? '' : '**:text-white!'
        ]"
      />

      <template #body>
        <UNavigationMenu
          orientation="vertical"
          :items="navItems.map(item => ({
            ...item,
            onClick: (e) => { e.preventDefault(); scrollToSection(item.to) }
          }))"
          :class="[
            'transition-colors duration-500 text-center',
            scrolled ? '' : '**:text-white!'
          ]"
        />
      </template>

      <template #right>
        <UButton
          label="Solicitar Cita"
          :color="scrolled ? 'primary' : 'white'"
          :variant="scrolled ? 'solid' : 'outline'"
          size="sm"
          class="hidden sm:flex transition-all duration-500"
          :class="!scrolled ? 'border-white/30 text-white hover:bg-white/10' : ''"
          @click="scrollToSection('#contacto')"
        />

      </template>

      <template #toggle></template>

    </UHeader>

    <!-- <UModal
      v-model:open="mobileMenuOpen"
      title="Menú"
      :ui="{ content: 'max-w-xs' }"
    >
      <template #body>
        <nav class="flex flex-col gap-1">
          <UButton
            v-for="item in navItems"
            :key="item.to"
            :label="item.label"
            variant="ghost"
            color="neutral"
            size="lg"
            class="justify-start"
            @click="scrollToSection(item.to)"
          />
          <UButton
            label="Solicitar Cita"
            color="primary"
            variant="solid"
            size="lg"
            class="mt-3"
            @click="scrollToSection('#contacto')"
          />
        </nav>
      </template>
    </UModal> -->

    <UMain>
      <NuxtPage />
    </UMain>

    <AppFooter />

    <!-- <a
      href="https://wa.me/"
      target="_blank"
      rel="noopener noreferrer"
      class="whatsapp-float"
      aria-label="Contáctenos por WhatsApp"
    >
      <svg
        width="28"
        height="28"
        viewBox="0 0 24 24"
        fill="white"
      >
        <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z" />
      </svg>
    </a> -->
  </UApp>
</template>
