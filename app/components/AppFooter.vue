<script setup>
const services = [
  'Consulta Externa',
  'Laboratorio Clínico',
  'Imágenes Diagnósticas',
  'Transporte Asistencial',
  'Atención Domiciliaria'
]

function scrollTo(href) {
  const el = document.querySelector(href)
  if (el) el.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <footer class="bg-clinic-dark border-t border-white/5">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8 py-20">
      <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-12 lg:gap-16">
        <div class="sm:col-span-2 lg:col-span-1">
          <div class="flex items-center gap-3 mb-6">
            <div class="w-12 h-12 bg-clinic-primary rounded-xl flex items-center justify-center shadow-lg shadow-clinic-primary/20">
              <span class="text-white font-heading font-bold text-xl">SJ</span>
            </div>
            <div>
              <span class="font-heading font-bold text-white text-xl leading-tight block">Clínica</span>
              <span class="font-heading font-semibold text-gray-500 text-sm leading-tight block">San Jorge</span>
            </div>
          </div>
          <p class="text-gray-500 text-sm leading-relaxed mb-8 max-w-xs">
            Institución de salud comprometida con la calidad y la excelencia en el cuidado de nuestros pacientes.
          </p>
          <div class="flex gap-3">
            <a
              href="#"
              class="w-11 h-11 bg-white/5 hover:bg-clinic-primary rounded-xl flex items-center justify-center transition-all duration-300 border border-white/5 hover:border-clinic-primary/30"
              aria-label="Facebook"
            >
              <UIcon
                name="i-lucide-facebook"
                class="w-5 h-5 text-gray-400 hover:text-white"
              />
            </a>
            <a
              href="#"
              class="w-11 h-11 bg-white/5 hover:bg-clinic-primary rounded-xl flex items-center justify-center transition-all duration-300 border border-white/5 hover:border-clinic-primary/30"
              aria-label="Instagram"
            >
              <UIcon
                name="i-lucide-instagram"
                class="w-5 h-5 text-gray-400 hover:text-white"
              />
            </a>
            <a
              href="#"
              class="w-11 h-11 bg-white/5 hover:bg-clinic-secondary rounded-xl flex items-center justify-center transition-all duration-300 border border-white/5 hover:border-clinic-secondary/30"
              aria-label="WhatsApp"
            >
              <UIcon
                name="i-lucide-message-circle"
                class="w-5 h-5 text-gray-400 hover:text-white"
              />
            </a>
          </div>
        </div>

        <div>
          <h4 class="font-heading font-bold text-white text-sm uppercase tracking-wider mb-6">
            Servicios
          </h4>
          <ul class="space-y-3.5">
            <li
              v-for="service in services"
              :key="service"
            >
              <a
                href="#servicios"
                class="text-gray-500 text-sm hover:text-clinic-secondary transition-colors duration-300 flex items-center gap-2 group"
                @click.prevent="scrollTo('#servicios')"
              >
                <div class="w-1 h-1 bg-gray-600 rounded-full group-hover:bg-clinic-secondary transition-colors" />
                {{ service }}
              </a>
            </li>
          </ul>
        </div>

        <div>
          <h4 class="font-heading font-bold text-white text-sm uppercase tracking-wider mb-6">
            Contacto
          </h4>
          <ul class="space-y-4">
            <li class="flex items-start gap-3">
              <UIcon
                name="i-lucide-phone"
                class="w-4 h-4 text-clinic-secondary mt-0.5 shrink-0"
              />
              <span class="text-gray-500 text-sm">+57 (XXX) XXX-XXXX</span>
            </li>
            <li class="flex items-start gap-3">
              <UIcon
                name="i-lucide-mail"
                class="w-4 h-4 text-clinic-secondary mt-0.5 shrink-0"
              />
              <span class="text-gray-500 text-sm">info@clinicasanjorge.com</span>
            </li>
            <li class="flex items-start gap-3">
              <UIcon
                name="i-lucide-map-pin"
                class="w-4 h-4 text-clinic-secondary mt-0.5 shrink-0"
              />
              <span class="text-gray-500 text-sm">Cali, Valle del Cauca</span>
            </li>
            <li class="flex items-start gap-3">
              <UIcon
                name="i-lucide-clock"
                class="w-4 h-4 text-clinic-secondary mt-0.5 shrink-0"
              />
              <span class="text-gray-500 text-sm">Lun - Vie: 7:00 AM - 7:00 PM</span>
            </li>
          </ul>
        </div>
      </div>
    </div>

    <div class="border-t border-white/5">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8 py-6">
        <div class="flex flex-col sm:flex-row items-center justify-between gap-4">
          <p class="text-gray-600 text-sm">
            &copy; {{ new Date().getFullYear() }} Clínica San Jorge S.A.S. Todos los derechos reservados.
          </p>
          <div class="flex gap-6">
            <a
              href="#"
              class="text-gray-600 text-xs hover:text-gray-400 transition-colors"
            >Política de Privacidad</a>
            <a
              href="#"
              class="text-gray-600 text-xs hover:text-gray-400 transition-colors"
            >Términos</a>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>
