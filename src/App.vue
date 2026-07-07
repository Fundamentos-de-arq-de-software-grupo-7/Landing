<template>
  <div class="min-h-screen bg-white text-slate-800 font-sans scroll-smooth">
    <!-- Navbar -->
    <nav class="flex items-center justify-between px-10 py-6 border-b border-slate-50 sticky top-0 bg-white/90 backdrop-blur z-50">
      <div class="flex items-center">
        <img :src="logoUrl" alt="MealFlow Logo" class="h-16 w-auto" />
      </div>
      <div class="hidden md:flex items-center gap-8 font-medium text-sm">
        <a href="#features" class="hover:text-emerald-500 transition">{{ t.nav.features }}</a>
        <a href="#stats" class="hover:text-emerald-500 transition">{{ t.nav.results }}</a>
        <a href="#plans" class="hover:text-emerald-500 transition">{{ t.nav.plans }}</a>
        <a href="#faq" class="hover:text-emerald-500 transition">FAQ</a>
        
        <select v-model="lang" class="bg-slate-100 px-3 py-1.5 rounded-lg border border-slate-200 cursor-pointer font-bold text-slate-700 focus:outline-none focus:border-emerald-500">
          <option value="es">ES 🇪🇸</option>
          <option value="en">EN 🇺🇸</option>
        </select>

        <a href="" class="bg-emerald-500 text-white px-6 py-2.5 rounded-full font-bold hover:bg-emerald-600 transition">
          {{ t.nav.demo }}
        </a>
      </div>
    </nav>

    <!-- Hero -->
    <header class="py-24 px-10 text-center bg-gradient-to-b from-emerald-50/50 to-white">
      <h1 class="text-7xl font-extrabold mb-8 text-slate-900 tracking-tight">
        {{ t.hero.title1 }} <br><span class="text-emerald-500">{{ t.hero.titleHighlight }}</span>
      </h1>
      <p class="text-xl text-slate-500 max-w-2xl mx-auto mb-10">
        {{ t.hero.desc }}
      </p>
      <div class="flex justify-center gap-4">
        <a href="#contact" class="bg-emerald-500 text-white px-10 py-4 rounded-xl font-bold text-lg hover:bg-emerald-600 transition shadow-lg shadow-emerald-200 text-center">
          {{ t.hero.btnStart }}
        </a>
        <button class="border-2 border-slate-200 px-10 py-4 rounded-xl font-bold text-lg hover:border-emerald-500 transition bg-white">
          {{ t.hero.btnDemo }}
        </button>
      </div>
    </header>

    <!-- Stats -->
    <section id="stats" class="py-16 border-y border-slate-100 bg-white">
      <div class="max-w-6xl mx-auto grid grid-cols-2 md:grid-cols-4 gap-8 text-center">
        <div v-for="stat in t.stats" :key="stat.label">
          <div class="text-4xl font-black text-emerald-500 mb-2">{{ stat.value }}</div>
          <div class="text-slate-500 text-sm font-medium uppercase tracking-widest">{{ stat.label }}</div>
        </div>
      </div>
    </section>

    <!-- Features -->
    <section id="features" class="py-24 max-w-6xl mx-auto px-10">
      <h2 class="text-4xl font-bold text-center mb-16">{{ t.features.sectionTitle }}</h2>
      <div class="grid md:grid-cols-3 gap-8">
        <div v-for="feat in t.features.list" :key="feat.title" class="p-8 border border-slate-100 rounded-3xl hover:border-emerald-200 transition bg-white shadow-sm hover:shadow-xl">
          <div class="text-emerald-500 text-4xl mb-6">{{ feat.icon }}</div>
          <h3 class="text-xl font-bold mb-3">{{ feat.title }}</h3>
          <p class="text-slate-500 text-sm leading-relaxed">{{ feat.desc }}</p>
        </div>
      </div>
    </section>

    <!-- Testimonials -->
    <section class="py-24 bg-slate-900 text-white px-10">
      <h2 class="text-4xl font-bold text-center mb-16">{{ t.testimonials.sectionTitle }}</h2>
      <div class="max-w-4xl mx-auto grid md:grid-cols-2 gap-8">
        <div v-for="tItem in t.testimonials.list" :key="tItem.name" class="p-8 bg-slate-800 rounded-3xl">
          <p class="text-lg italic mb-6">"{{ tItem.quote }}"</p>
          <div class="font-bold text-emerald-400">{{ tItem.name }}</div>
          <div class="text-sm text-slate-400">{{ tItem.role }}</div>
        </div>
      </div>
    </section>

    <!-- Plans -->
    <section id="plans" class="py-24 px-10">
      <h2 class="text-4xl font-bold text-center mb-16">{{ t.plans.sectionTitle }}</h2>
      <div class="max-w-4xl mx-auto grid md:grid-cols-2 gap-8 justify-center">
        <div v-for="plan in t.plans.list" :key="plan.name" :class="plan.highlight ? 'border-2 border-emerald-500 shadow-xl shadow-emerald-50' : 'border border-slate-200'" class="p-8 rounded-3xl bg-white relative">
          <h3 class="text-2xl font-bold">{{ plan.name }}</h3>
          <div class="text-5xl font-black my-6">{{ plan.price }}</div>
          <ul class="space-y-4 mb-8 text-slate-600">
            <li v-for="item in plan.features" :key="item" class="flex items-center gap-2">
              <span class="text-emerald-500 font-bold">✓</span> {{ item }}
            </li>
          </ul>
          <a href="#contact" class="block w-full text-center py-4 rounded-xl font-bold transition" :class="plan.highlight ? 'bg-emerald-500 text-white hover:bg-emerald-600' : 'bg-slate-100 hover:bg-slate-200'">
            {{ t.plans.btnLabel }}
          </a>
        </div>
      </div>
    </section>

    <!-- FAQ -->
    <section id="faq" class="py-24 px-10 bg-slate-50">
      <h2 class="text-4xl font-bold text-center mb-16">{{ t.faq.sectionTitle }}</h2>
      <div class="max-w-3xl mx-auto space-y-6">
        <div v-for="item in t.faq.list" :key="item.q" class="bg-white p-8 rounded-3xl border border-slate-200 shadow-sm">
          <h3 class="text-lg font-bold text-slate-900 mb-2">{{ item.q }}</h3>
          <p class="text-slate-500">{{ item.a }}</p>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-24 px-10 bg-white">
      <div class="max-w-4xl mx-auto">
        <h2 class="text-4xl font-bold text-center mb-4">¿Tienes alguna pregunta?</h2>
        <p class="text-center text-slate-500 mb-12">Déjanos tus datos y nos pondremos en contacto contigo.</p>
        <form @submit.prevent="submitContact" class="grid md:grid-cols-2 gap-6 bg-slate-50 p-8 rounded-3xl border border-slate-100">
          <input type="text" placeholder="Nombre" class="w-full p-4 rounded-xl border border-slate-200 focus:ring-2 focus:ring-emerald-500 outline-none" required />
          <input type="email" placeholder="Correo electrónico" class="w-full p-4 rounded-xl border border-slate-200 focus:ring-2 focus:ring-emerald-500 outline-none" required />
          <textarea placeholder="Tu mensaje" class="w-full p-4 rounded-xl border border-slate-200 focus:ring-2 focus:ring-emerald-500 outline-none md:col-span-2" rows="4" required></textarea>
          <button type="submit" class="md:col-span-2 bg-slate-900 text-white py-4 rounded-xl font-bold hover:bg-emerald-600 transition">Enviar mensaje</button>
        </form>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-slate-50 py-16 px-10 text-slate-500 text-sm border-t border-slate-100">
      <div class="max-w-6xl mx-auto grid md:grid-cols-4 gap-12">
        <div>
          <h4 class="font-bold text-slate-900 mb-4">MealFlow</h4>
          <p>{{ t.footer.tagline }}</p>
        </div>
        <div>
          <h4 class="font-bold text-slate-900 mb-4">{{ t.footer.col1Title }}</h4>
          <p class="mb-2 cursor-pointer hover:text-emerald-500">Features</p>
          <p class="mb-2 cursor-pointer hover:text-emerald-500">API</p>
          <p class="cursor-pointer hover:text-emerald-500">Security</p>
        </div>
        <div>
          <h4 class="font-bold text-slate-900 mb-4">{{ t.footer.col2Title }}</h4>
          <p class="mb-2 cursor-pointer hover:text-emerald-500">{{ t.footer.about }}</p>
          <p class="mb-2 cursor-pointer hover:text-emerald-500">{{ t.footer.careers }}</p>
          <p class="cursor-pointer hover:text-emerald-500">{{ t.footer.contact }}</p>
        </div>
        <div>
          <h4 class="font-bold text-slate-900 mb-4">{{ t.footer.col3Title }}</h4>
          <p class="mb-2 cursor-pointer hover:text-emerald-500">{{ t.footer.privacy }}</p>
          <p class="cursor-pointer hover:text-emerald-500">{{ t.footer.terms }}</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import logoUrl from './assets/logo.png';

const lang = ref('es');
const submitContact = () => { alert('¡Gracias! Nos pondremos en contacto pronto.'); };

const dictionary = {
  es: {
    nav: { features: 'Funcionalidades', results: 'Resultados', plans: 'Planes', demo: 'Request Demo' },
    hero: {
      title1: 'El futuro de la gestión de',
      titleHighlight: 'viandas nutricionales.',
      desc: 'Optimiza tu cocina, automatiza tus ventas y escala tu negocio nutricional con nuestra plataforma 100% Cloud.',
      btnStart: 'Comenzar ahora',
      btnDemo: 'Ver Demo Técnica'
    },
    stats: [
      { value: '+500', label: 'Negocios activos' },
      { value: '99.9%', label: 'Uptime Cloud' },
      { value: '+1M', label: 'Viandas gestionadas' },
      { value: '24/7', label: 'Soporte técnico' }
    ],
    features: {
      sectionTitle: 'Features de nivel profesional',
      list: [
        { icon: '🥗', title: 'Catalog-Service', desc: 'Ajuste de macros inteligente y en tiempo real para cada cliente.' },
        { icon: '🔔', title: 'Gestión de Pedidos', desc: 'Logística integrada con notificaciones push para entregas sin errores.' },
        { icon: '☁️', title: 'API Gateway', desc: 'Integración total con tus herramientas de pago, CRM y entrega.' }
      ]
    },
    testimonials: {
      sectionTitle: 'Lo que dicen los dueños de negocios',
      list: [
        { name: 'María García', role: 'CEO NutriEat', quote: 'MealFlow transformó nuestra logística. Pasamos de gestionar pedidos en Excel a hacerlo todo automático.' },
        { name: 'Carlos Ruiz', role: 'Founder HealthyBox', quote: 'La mejor decisión tecnológica que tomamos. Escalamos un 300% en 6 meses.' }
      ]
    },
    plans: {
      sectionTitle: 'Planes para tu crecimiento',
      btnLabel: 'Contratar',
      list: [
        { name: 'Starter', price: '$0', features: ['50 viandas/mes', 'Soporte email', 'Dashboard básico'], highlight: false },
        { name: 'Pro', price: '$49', features: ['Ilimitado', 'Notificaciones real-time', 'API Access', 'Reportes'], highlight: true },
      ]
    },
    faq: {
      sectionTitle: 'Preguntas Frecuentes',
      list: [
        { q: '¿Tienen contrato de permanencia?', a: 'No, puedes cancelar en cualquier momento sin penalizaciones.' },
        { q: '¿Puedo cambiar de plan?', a: 'Sí, puedes escalar o reducir tu plan desde tu panel en cualquier momento.' }
      ]
    },
    footer: {
      tagline: 'La solución definitiva para negocios de distribución nutricional.',
      col1Title: 'Producto',
      col2Title: 'Empresa',
      col3Title: 'Legal',
      about: 'Sobre nosotros',
      careers: 'Carreras',
      contact: 'Contacto',
      privacy: 'Privacidad',
      terms: 'Términos'
    }
  },
  en: {
    nav: { features: 'Features', results: 'Results', plans: 'Plans', demo: 'Request Demo' },
    hero: {
      title1: 'The future of managing',
      titleHighlight: 'nutritional meals.',
      desc: 'Optimize your kitchen, automate your sales, and scale your nutritional business with our 100% Cloud platform.',
      btnStart: 'Get started now',
      btnDemo: 'View Technical Demo'
    },
    stats: [
      { value: '+500', label: 'Active businesses' },
      { value: '99.9%', label: 'Cloud Uptime' },
      { value: '+1M', label: 'Meals managed' },
      { value: '24/7', label: 'Technical support' }
    ],
    features: {
      sectionTitle: 'Professional Level Features',
      list: [
        { icon: '🥗', title: 'Catalog-Service', desc: 'Intelligent, real-time macro adjustments for each client.' },
        { icon: '🔔', title: 'Order Management', desc: 'Integrated logistics with push notifications for error-free deliveries.' },
        { icon: '☁️', title: 'API Gateway', desc: 'Full integration with your payment, CRM, and delivery tools.' }
      ]
    },
    testimonials: {
      sectionTitle: 'What business owners are saying',
      list: [
        { name: 'María García', role: 'CEO NutriEat', quote: 'MealFlow transformed our logistics. We went from managing orders in Excel to doing it all automatically.' },
        { name: 'Carlos Ruiz', role: 'Founder HealthyBox', quote: 'The best technological decision we ever made. We scaled 300% in 6 months.' }
      ]
    },
    plans: {
      sectionTitle: 'Plans for your growth',
      btnLabel: 'Choose Plan',
      list: [
        { name: 'Starter', price: '$0', features: ['50 meals/month', 'Email support', 'Basic dashboard'], highlight: false },
        { name: 'Pro', price: '$49', features: ['Unlimited', 'Real-time notifications', 'API Access', 'Reports'], highlight: true },
      ]
    },
    faq: {
      sectionTitle: 'Frequently Asked Questions',
      list: [
        { q: 'Do you have a lock-in contract?', a: 'No, you can cancel at any time without penalties.' },
        { q: 'Can I change my plan?', a: 'Yes, you can upgrade or downgrade your plan from your dashboard at any time.' }
      ]
    },
    footer: {
      tagline: 'The ultimate solution for meal prep and nutrition distribution businesses.',
      col1Title: 'Product',
      col2Title: 'Company',
      col3Title: 'Legal',
      about: 'About us',
      careers: 'Careers',
      contact: 'Contact',
      privacy: 'Privacy Policy',
      terms: 'Terms of Service'
    }
  }
};

const t = computed(() => dictionary[lang.value]);
</script>