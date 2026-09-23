<script setup>
const values = [
  { icon: 'i-lucide-heart-handshake', title: 'Humanización', description: 'Trato cálido y compasivo en cada interacción.' },
  { icon: 'i-lucide-zap', title: 'Eficiencia', description: 'Atención oportuna con los más altos estándares.' },
  { icon: 'i-lucide-shield', title: 'Seguridad', description: 'Protocolos rigurosos en cada procedimiento.' },
  { icon: 'i-lucide-handshake', title: 'Transparencia', description: 'Honestidad y disposición permanente.' }
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
    { threshold: 0.08 }
  )
  const el = document.getElementById('nosotros')
  if (el) observer.observe(el)
})
</script>

<template>
  <section
    id="nosotros"
    class="py-28 lg:py-36 relative overflow-hidden"
  >
    <div class="absolute top-0 right-0 w-125 h-125 bg-clinic-accent/20 rounded-full blur-[120px] pointer-events-none" />

    <div class="container mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div class="grid lg:grid-cols-5 gap-12 lg:gap-20 items-center mb-28">
        <div
          :class="[
            'lg:col-span-3 transition-all duration-1000 ease-out',
            sectionVisible ? 'opacity-100 translate-x-0' : 'opacity-0 -translate-x-12'
          ]"
        >
          <div class="relative rounded-3xl overflow-hidden shadow-2xl shadow-clinic-primary/10">
            <img
              src="/img/FOTO 5.jpeg"
              alt="Clínica San Jorge - Atención médica"
              class="w-full h-100 sm:h-120 object-cover"
              loading="lazy"
            >
            <div class="absolute inset-0 bg-linear-to-t from-clinic-primary/50 via-transparent to-transparent" />
            <div class="absolute bottom-0 left-0 right-0 p-8">
              <div class="glass-card rounded-2xl p-5 max-w-sm">
                <p class="font-heading font-semibold text-black text-sm leading-relaxed">
                  "Aliado confiable en el cuidado de tu salud"
                </p>
              </div>
            </div>
          </div>
        </div>

        <div
          :class="[
            'lg:col-span-2 transition-all duration-1000 ease-out delay-200',
            sectionVisible ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-12'
          ]"
        >
          <div class="inline-flex items-center gap-2 bg-clinic-primary/5 rounded-full px-4 py-1.5 mb-6">
            <div class="w-1.5 h-1.5 bg-clinic-primary rounded-full" />
            <span class="text-clinic-primary text-sm font-semibold tracking-wide uppercase">Quiénes Somos</span>
          </div>

          <h2
            class="font-heading text-3xl sm:text-4xl font-bold text-clinic-dark mb-6"
            style="text-wrap: balance;"
          >
            Años <span class="gradient-text">cuidando familias</span>
          </h2>

          <div class="flex 2xl:flex-row flex-col gap-4">
            <div class="flex-1 bg-clinic-light rounded-2xl p-5 border border-clinic-muted/30">
              <div class="font-heading font-bold text-clinic-primary text-lg mb-1">
                Misión
              </div>
              <p class="text-clinic-gray text-sm leading-relaxed lowercase">
                LA CLINICA SAN JORGE SAS, ESTÁ COMPROMETIDA CON LA CONDICIÓN Y SEGURIDAD DEL PACIENTE, LA FAMILIA, EL MEDIO AMBIENTE, EL BIENESTAR LABORAL Y LA FORMACIÓN ACADÉMICA; BUSCANDO PRESERVAR Y MEJORAR LA CALIDAD DE VIDA CON RESPONSABILIDAD SOCIAL.
              </p>
            </div>
            <div class="flex-1 bg-clinic-light rounded-2xl p-5 border border-clinic-muted/30">
              <div class="font-heading font-bold text-clinic-secondary text-lg mb-1">
                Visión
              </div>
              <p class="text-clinic-gray text-sm leading-relaxed lowercase">
                LA CLINICA SAN JORGE SAS, SERÁ EN EL 2028 UNA IPS RECONOCIDAEN LA REGIÓN POR LA ACREDITACIÓN DE LOS SERVICIOS DE SALUD,GRACIAS AL TRABAJO EN ALTOS ESTÁNDARES DE CALIDADCUMPLIDOS, EN UN MARCO DE SEGURIDAD Y CONFIANZA.
              </p>
            </div>
          </div>
        </div>
      </div>

      <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-5">
        <div
          v-for="(value, index) in values"
          :key="index"
          :class="[
            'group bg-clinic-white rounded-2xl p-6 border border-clinic-muted/30 text-center bento-item',
            sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
          :style="{ transitionDelay: `${400 + index * 100}ms` }"
        >
          <div class="w-14 h-14 bg-clinic-primary/5 group-hover:bg-clinic-primary/10 rounded-2xl flex items-center justify-center mx-auto mb-4 transition-all duration-300 group-hover:scale-110">
            <UIcon
              :name="value.icon"
              class="w-7 h-7 text-clinic-primary"
            />
          </div>
          <h4 class="font-heading font-bold text-clinic-dark mb-2">
            {{ value.title }}
          </h4>
          <p class="text-sm text-clinic-gray leading-relaxed">
            {{ value.description }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>
