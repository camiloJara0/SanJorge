<script setup>
const contactInfo = [
  { icon: 'i-lucide-phone', label: 'Teléfono', value: '+57 (XXX) XXX-XXXX', href: 'tel:' },
  { icon: 'i-lucide-mail', label: 'Email', value: 'info@clinicasanjorge.com', href: 'mailto:info@clinicasanjorge.com' },
  { icon: 'i-lucide-map-pin', label: 'Dirección', value: 'Cali, Valle del Cauca', href: '#' },
  { icon: 'i-lucide-clock', label: 'Horarios', value: 'Lun - Vie: 7:00 AM - 7:00 PM', href: null }
]

const formData = reactive({ name: '', phone: '', service: '', message: '' })
const submitted = ref(false)
const loading = ref(false)

function handleSubmit() {
  loading.value = true
  setTimeout(() => {
    loading.value = false
    submitted.value = true
    setTimeout(() => {
      submitted.value = false
    }, 5000)
  }, 1500)
}

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
  const el = document.getElementById('contacto')
  if (el) observer.observe(el)
})
</script>

<template>
  <section
    id="contacto"
    class="relative overflow-hidden"
  >
    <div class="absolute inset-0 bg-clinic-dark" />
    <div class="absolute top-0 right-0 w-125 h-125 bg-clinic-primary/8 rounded-full blur-[150px] pointer-events-none" />
    <div class="absolute bottom-0 left-0 w-100 h-100 bg-clinic-secondary/5 rounded-full blur-[120px] pointer-events-none" />

    <div class="relative z-10 py-28 lg:py-36">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div
          :class="[
            'text-center mb-20 transition-all duration-800 ease-out',
            sectionVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
        >
          <div class="inline-flex items-center gap-2 bg-clinic-secondary/10 rounded-full px-4 py-1.5 mb-6 border border-clinic-secondary/20">
            <div class="w-1.5 h-1.5 bg-clinic-secondary rounded-full" />
            <span class="text-clinic-secondary text-sm font-semibold tracking-wide uppercase">Contacto</span>
          </div>
          <h2 class="font-heading text-3xl sm:text-4xl lg:text-5xl font-bold text-white mb-5">
            Estamos <span class="text-clinic-secondary">para servirte</span>
          </h2>
          <p class="text-lg text-gray-400 max-w-2xl mx-auto">
            Solicita tu cita o resuelve cualquier inquietud. Nuestro equipo está listo.
          </p>
        </div>

        <div class="grid lg:grid-cols-2 gap-12 lg:gap-20 items-start">
          <div
            :class="[
              'transition-all duration-1000 ease-out',
              sectionVisible ? 'opacity-100 translate-x-0' : 'opacity-0 -translate-x-12'
            ]"
          >
            <div class="space-y-7 mb-12">
              <div
                v-for="(info, index) in contactInfo"
                :key="index"
                class="group flex items-start gap-4"
              >
                <div class="w-13 h-13 bg-white/5 group-hover:bg-clinic-primary/15 rounded-2xl flex items-center justify-center shrink-0 transition-all duration-300 border border-white/5">
                  <UIcon
                    :name="info.icon"
                    class="w-5 h-5 text-clinic-secondary"
                  />
                </div>
                <div>
                  <div class="text-gray-500 text-sm mb-0.5">
                    {{ info.label }}
                  </div>
                  <component
                    :is="info.href ? 'a' : 'div'"
                    :href="info.href"
                    class="font-heading font-semibold text-white hover:text-clinic-secondary transition-colors text-lg"
                  >
                    {{ info.value }}
                  </component>
                </div>
              </div>
            </div>

            <div class="rounded-2xl overflow-hidden border border-white/10 h-64 bg-white/5">
              <iframe
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3976.5!2d-76.53!3d3.45!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zM8KwMjcnMDAuMCJOIDc2wrAzMSc0OC4wIlc!5e0!3m2!1ses!2sco!4v1"
                width="100%"
                height="100%"
                style="border:0; filter: grayscale(0.6) contrast(1.1);"
                allowfullscreen
                loading="lazy"
                referrerpolicy="no-referrer-when-downgrade"
                title="Ubicación de Clínica San Jorge"
              />
            </div>
          </div>

          <div
            :class="[
              'transition-all duration-1000 ease-out delay-200',
              sectionVisible ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-12'
            ]"
          >
            <div class="glass-card-dark rounded-3xl p-8 sm:p-10 form-glow">
              <h3 class="font-heading font-bold text-white text-2xl mb-2">
                Solicita tu cita
              </h3>
              <p class="text-gray-400 text-sm mb-8">
                Completa el formulario y te contactaremos.
              </p>

              <div v-if="!submitted">
                <form
                  class="space-y-5"
                  @submit.prevent="handleSubmit"
                >
                  <div>
                    <label class="block text-gray-400 text-sm mb-2 font-medium">Nombre completo</label>
                    <div class="relative">
                      <UIcon
                        name="i-lucide-user"
                        class="absolute left-4 top-1/2 -translate-y-1/2 w-4 h-4 text-gray-500"
                      />
                      <input
                        v-model="formData.name"
                        type="text"
                        placeholder="Tu nombre"
                        required
                        class="w-full bg-white/5 border border-white/10 rounded-xl px-11 py-3.5 text-white placeholder-gray-600 focus:outline-none focus:border-clinic-secondary/50 focus:ring-1 focus:ring-clinic-secondary/30 transition-all"
                      >
                    </div>
                  </div>

                  <div>
                    <label class="block text-gray-400 text-sm mb-2 font-medium">Teléfono</label>
                    <div class="relative">
                      <UIcon
                        name="i-lucide-phone"
                        class="absolute left-4 top-1/2 -translate-y-1/2 w-4 h-4 text-gray-500"
                      />
                      <input
                        v-model="formData.phone"
                        type="tel"
                        placeholder="+57 XXX XXX XXXX"
                        required
                        class="w-full bg-white/5 border border-white/10 rounded-xl px-11 py-3.5 text-white placeholder-gray-600 focus:outline-none focus:border-clinic-secondary/50 focus:ring-1 focus:ring-clinic-secondary/30 transition-all"
                      >
                    </div>
                  </div>

                  <div>
                    <label class="block text-gray-400 text-sm mb-2 font-medium">Servicio de interés</label>
                    <div class="relative">
                      <UIcon
                        name="i-lucide-stethoscope"
                        class="absolute left-4 top-1/2 -translate-y-1/2 w-4 h-4 text-gray-500"
                      />
                      <select
                        v-model="formData.service"
                        class="w-full bg-white/5 border border-white/10 rounded-xl px-11 py-3.5 text-white focus:outline-none focus:border-clinic-secondary/50 focus:ring-1 focus:ring-clinic-secondary/30 transition-all appearance-none"
                      >
                        <option
                          value=""
                          disabled
                          selected
                          class="text-clinic-dark"
                        >
                          Selecciona un servicio
                        </option>
                        <option
                          value="general"
                          class="text-clinic-dark"
                        >
                          Consulta General
                        </option>
                        <option
                          value="laboratorio"
                          class="text-clinic-dark"
                        >
                          Laboratorio Clínico
                        </option>
                        <option
                          value="imagenes"
                          class="text-clinic-dark"
                        >
                          Imágenes Diagnósticas
                        </option>
                        <option
                          value="transporte"
                          class="text-clinic-dark"
                        >
                          Transporte Asistencial
                        </option>
                        <option
                          value="domiciliaria"
                          class="text-clinic-dark"
                        >
                          Atención Domiciliaria
                        </option>
                        <option
                          value="pediatrico"
                          class="text-clinic-dark"
                        >
                          Pediátrico
                        </option>
                        <option
                          value="otra"
                          class="text-clinic-dark"
                        >
                          Otra especialidad
                        </option>
                      </select>
                      <UIcon
                        name="i-lucide-chevron-down"
                        class="absolute right-4 top-1/2 -translate-y-1/2 w-4 h-4 text-gray-500 pointer-events-none"
                      />
                    </div>
                  </div>

                  <div>
                    <label class="block text-gray-400 text-sm mb-2 font-medium">Mensaje</label>
                    <textarea
                      v-model="formData.message"
                      placeholder="Cuéntanos cómo podemos ayudarte..."
                      rows="3"
                      class="w-full bg-white/5 border border-white/10 rounded-xl px-4 py-3.5 text-white placeholder-gray-600 focus:outline-none focus:border-clinic-secondary/50 focus:ring-1 focus:ring-clinic-secondary/30 transition-all resize-none"
                    />
                  </div>

                  <UButton
                    label="Enviar Solicitud"
                    icon="i-lucide-send"
                    color="secondary"
                    variant="solid"
                    size="lg"
                    block
                    type="submit"
                    :loading="loading"
                    class="mt-2"
                  />
                </form>
              </div>

              <div
                v-else
                class="text-center py-16 animate-scale-in"
              >
                <div class="w-16 h-16 bg-clinic-secondary/15 rounded-2xl flex items-center justify-center mx-auto mb-5">
                  <UIcon
                    name="i-lucide-check-circle"
                    class="w-8 h-8 text-clinic-secondary"
                  />
                </div>
                <h3 class="font-heading font-bold text-white text-xl mb-2">
                  ¡Solicitud enviada!
                </h3>
                <p class="text-gray-400">
                  Nos pondremos en contacto contigo pronto.
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
