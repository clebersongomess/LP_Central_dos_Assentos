<script setup>
import { ref } from 'vue'

const whatsappNumber = "5511945785565"
const defaultMessage = "Olá! Vim do site Central dos Assentos e gostaria de enviar a foto do meu vaso sanitário para vocês confirmarem o modelo exato para mim."
const waLink = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(defaultMessage)}`

// Marcas para o Slider
const marcas = [
  'Deca', 'Incepa', 'Celite', 'Icasa', 'Ideal Standard', 
  'Logasa', 'Fiori', 'Roca', 'Hervy', 'Eternit', 'Lorenzetti'
]

const topSellers = ref([
  {
    id: 1,
    name: 'Assento Acrílico Decorado Borboleta (Convencional)',
    description: 'Resina poliéster virgem, ferragem reforçada e batentes em PVC flexível. Design incolor elegante com elementos naturais.',
    price: 'R$ 279,99',
    images: ['/convencional-diagonal-rosa-01.jpeg', '/convencional-diagonal-rosa-02.jpeg', '/convencional-diagonal-rosa-03.jpeg'], 
    paymentLink: 'https://mpago.la/2M8YXe6'
  },
  {
    id: 2,
    name: 'Assento Decorado Glitter Resina Rosa (Oval)',
    description: 'Peça artesanal exclusiva. As borboletas dão um toque único. Compatível com Deca, Icasa e Celite.',
    price: 'R$ 356,99',
    images: ['/convencional-glitter-rosa-01.jpeg', '/convencional-glitter-rosa-02.jpeg'], 
    paymentLink: 'https://mpago.la/1MnJcxZ'
  },
  {
    id: 3,
    name: 'Assento Sabatini Laranja (Icasa)',
    description: 'Modelo específico para Icasa Sabatini. Dobradiças em aço garantem total segurança e estabilidade.',
    price: 'R$ 304,43', 
    images: ['/sabatini-laranja-01.png', 'sabatini-laranja-02.png', 'sabatini-laranja-03.png'],
    paymentLink: 'https://mpago.la/2iRiAKm'
  },
  {
    id: 4,
    name: 'Assento Convencional Decorado Tampas de Cerveja',
    description: 'Acabamento brilhante e alta durabilidade para vasos ovais. Renova o ambiente com muita sofisticação.',
    price: 'R$ 499,99', 
    images: ['/convencional-cerveja-01.png', 'convencional-cerveja-02.png', 'convencional-cerveja-03.png'],
    paymentLink: 'https://mpago.la/1T8bxPb'
  },
  {
    id: 5,
    name: 'Assento Decorado Belle Epoque Verde Tanslúcido',
    description: 'Sofisticação máxima com decoração praia. Transforma o visual do banheiro.',
    price: 'R$ 355,99',
    images: ['/belle-epoque-verde-01.png', 'belle-epoque-verde-02.png', 'belle-epoque-verde-03.png'],
    paymentLink: 'https://mpago.la/1vetgAN'
  },
  {
    id: 6,
    name: 'Assento Incepa Calypso Verde Mármore',
    description: 'Design efeito mármore na cor verde. Resina de altíssima qualidade e resistência.',
    price: 'R$ 405,72',
    images: ['/incepa-calypso-verde-01.png', 'incepa-calypso-verde-02.png', 'incepa-calypso-verde-03.png', 'incepa-calypso-verde-04.png'],
    paymentLink: 'https://mpago.la/1ewGUrY'
  }
])

// ESTADO DA GALERIA
const isGalleryOpen = ref(false)
const activeProduct = ref(null)
const activeImageIndex = ref(0)

const openGallery = (product) => {
  activeProduct.value = product
  activeImageIndex.value = 0
  isGalleryOpen.value = true
  document.body.style.overflow = 'hidden' 
}

const closeGallery = () => {
  isGalleryOpen.value = false
  activeProduct.value = null
  document.body.style.overflow = 'auto' 
}

const nextImage = () => {
  if (activeProduct.value) {
    activeImageIndex.value = (activeImageIndex.value + 1) % activeProduct.value.images.length
  }
}

const prevImage = () => {
  if (activeProduct.value) {
    activeImageIndex.value = (activeImageIndex.value - 1 + activeProduct.value.images.length) % activeProduct.value.images.length
  }
}
</script>

<template>
  <div class="min-h-screen bg-gray-50 font-sans text-gray-800">
    
    <div class="sticky top-0 z-[60] bg-green-600 text-white text-center py-2 px-4 shadow-lg border-b border-green-700">
      <div class="max-w-7xl mx-auto flex flex-col md:flex-row items-center justify-center gap-1 md:gap-3">
        <div class="flex items-center gap-2 font-bold text-sm tracking-wide">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path d="M8 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0zM15 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0z" />
            <path d="M3 4a1 1 0 00-1 1v10a1 1 0 001 1h1.05a2.5 2.5 0 014.9 0H10a1 1 0 001-1V5a1 1 0 00-1-1H3zM14 7a1 1 0 00-1 1v6.05A2.5 2.5 0 0115.95 16H17a1 1 0 001-1v-5a1 1 0 00-.293-.707l-2-2A1 1 0 0015 7h-1z" />
          </svg>
          <span>FRETE GRÁTIS EM TODOS OS PRODUTOS!</span>
        </div>
        <span class="text-[10px] md:text-xs font-medium opacity-90 bg-green-700/50 px-2 py-0.5 rounded-full">
          *Exceto regiões Norte e Centro-Oeste
        </span>
      </div>
    </div>

    <header class="bg-blue-900 text-white text-center py-12 px-4">
      <img 
        src="/logo-central-dos-assentos.png" 
        alt="Logo Central dos Assentos" 
        class="w-40 h-40 md:w-48 md:h-48 object-contain mx-auto mb-8 rounded-3xl shadow-2xl border-4 border-blue-800 bg-white p-2"
      >
      <h1 class="text-4xl md:text-5xl font-bold mb-2 tracking-tight">Central dos Assentos</h1>
      <p class="text-lg md:text-xl text-blue-200 max-w-2xl mx-auto mb-8 font-light">
        Escolha o design que você ama. Nós fabricamos no <span class="text-white font-bold underline decoration-yellow-400">formato exato</span> do seu vaso.
      </p>
      
      <div class="bg-blue-800/50 p-6 rounded-xl max-w-3xl mx-auto border border-blue-700 mb-8">
        <h3 class="text-xl font-bold text-yellow-400 mb-2 font-sans">Como comprar o modelo correto?</h3>
        <p class="text-blue-100 mb-4 text-sm md:text-base">Não se preocupe com marcas ou medidas. Basta nos enviar uma foto do seu vaso no WhatsApp que fabricamos a peça com o encaixe perfeito.</p>
        <a :href="waLink" target="_blank" class="bg-green-500 hover:bg-green-600 transition-all hover:scale-105 text-white font-bold py-3 px-8 rounded-lg shadow-lg flex items-center justify-center w-fit mx-auto gap-2 no-underline">
          Chamar no WhatsApp e enviar foto
        </a>
      </div>
    </header>

    <section class="bg-blue-50 py-8 border-b border-blue-100">
      <div class="max-w-4xl mx-auto px-4 text-center">
        <div class="inline-flex items-center justify-center p-2 bg-blue-100 rounded-full mb-4">
          <span class="text-blue-700 text-xs font-bold uppercase px-3">Diferencial Único</span>
        </div>
        <h2 class="text-2xl font-bold text-blue-900 mb-3">Qualquer modelo, para qualquer vaso.</h2>
        <p class="text-gray-600 leading-relaxed">
          Gostou de uma estampa mas seu vaso é de um modelo específico (como <strong>Thema, Bali, Monte Carlo ou Nexo</strong>)? <br class="hidden md:block" /> 
          Nós fabricamos todos os nossos modelos decorados para <strong>todas as marcas do mercado.</strong>
        </p>
      </div>
    </section>

    <section class="bg-white border-b border-gray-200 py-6 overflow-hidden">
      <div class="relative flex overflow-x-hidden">
        <div class="animate-marquee whitespace-nowrap flex items-center">
          <span v-for="marca in [...marcas, ...marcas]" :key="marca" class="mx-8 text-xl md:text-2xl font-black text-gray-200 uppercase">
            {{ marca }}
          </span>
        </div>
      </div>
    </section>

    <main class="max-w-7xl mx-auto py-16 px-4">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div v-for="product in topSellers" :key="product.id" class="bg-white rounded-xl shadow-md overflow-hidden hover:shadow-xl transition-shadow border border-gray-100 flex flex-col group relative">
          
          <span class="absolute top-4 left-4 bg-green-500 text-white text-[10px] font-extrabold uppercase tracking-wider px-2 py-1 rounded shadow-md z-10">
            Frete Grátis*
          </span>

          <div class="overflow-hidden relative cursor-pointer aspect-square" @click="openGallery(product)">
             <img :src="product.images[0]" :alt="product.name" class="w-full h-full object-contain p-4 bg-white group-hover:scale-105 transition-transform duration-300">
             <div class="absolute inset-0 bg-blue-900/0 group-hover:bg-blue-900/5 transition-colors flex items-center justify-center">
                <span class="bg-white/90 text-blue-900 px-4 py-2 rounded-full text-xs font-bold opacity-0 group-hover:opacity-100 transition-opacity shadow-sm">Ver fotos reais</span>
             </div>
          </div>
          
          <div class="p-6 flex flex-col flex-grow text-center">
            <h3 class="text-lg font-bold text-gray-800 mb-1 font-sans leading-tight">{{ product.name }}</h3>
            <p class="text-[10px] text-blue-600 font-bold uppercase mb-3">✓ Fabricamos para qualquer marca</p>
            
            <p class="text-gray-600 text-xs mb-6 flex-grow leading-relaxed">{{ product.description }}</p>
            <div class="mt-auto border-t border-gray-100 pt-4">
              <span class="block text-2xl font-black text-blue-900 mb-4 font-sans">{{ product.price }}</span>
              <a :href="product.paymentLink" target="_blank" class="block w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-3 rounded-lg shadow-md transition-colors no-underline">
                Comprar Agora
              </a>
            </div>
          </div>
        </div>
      </div>
    </main>

    <section class="bg-gray-100 py-8 border-b border-gray-200">
      <div class="max-w-7xl mx-auto px-4">
        <div class="flex flex-col md:flex-row items-center justify-center gap-8 md:gap-16">
          
          <div class="flex items-center gap-4 group">
            <div class="bg-yellow-400 p-3 rounded-full shadow-md group-hover:scale-110 transition-transform">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-blue-900" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
              </svg>
            </div>
            <div class="text-center md:text-left">
              <h4 class="font-black text-gray-800 leading-tight">Mercado Líder</h4>
              <p class="text-xs text-gray-500 uppercase tracking-tighter">Um dos melhores do site</p>
            </div>
          </div>

          <div class="flex items-center gap-4 group">
            <div class="bg-orange-500 p-3 rounded-full shadow-md group-hover:scale-110 transition-transform">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-white" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
              </svg>
            </div>
            <div class="text-center md:text-left">
              <h4 class="font-black text-gray-800 leading-tight">Shopee Indica</h4>
              <p class="text-xs text-gray-500 uppercase tracking-tighter">Vendedor de confiança</p>
            </div>
          </div>

          <div class="flex items-center gap-4 group">
            <div class="bg-blue-900 p-3 rounded-full shadow-md group-hover:scale-110 transition-transform">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-white" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M3 21v-9a4 4 0 1 1 8 0v9M13 21V3a2 2 0 0 1 2-2h5a2 2 0 0 1 2 2v18"/>
                <path d="M3 7h18M3 11h18M3 15h18"/>
              </svg>
            </div>
            <div class="text-center md:text-left">
              <h4 class="font-black text-gray-800 leading-tight">Direto de Fábrica</h4>
              <p class="text-xs text-gray-500 uppercase tracking-tighter">Grupo CAG Assentos</p>
            </div>
          </div>

        </div>
      </div>
    </section>

    <footer class="bg-gray-900 text-gray-400 text-center py-10 border-t-4 border-blue-900">
      <p class="text-sm">
        &copy; 2026 Central dos Assentos. Todos os direitos reservados.<br />
        Uma empresa do grupo <strong class="text-gray-200">CAG Assentos Sanitários</strong>.
      </p>
      <p class="text-[10px] mt-4 opacity-50 max-w-md mx-auto px-4 italic">
        *A promoção de frete grátis é válida para as regiões Sul e Sudeste. Consulte condições para demais localidades no momento do checkout.
      </p>
    </footer>

    <div v-if="isGalleryOpen && activeProduct" class="fixed inset-0 z-[100] flex items-center justify-center bg-black/95 backdrop-blur-sm p-4">
      <button @click="closeGallery" class="absolute top-6 right-6 text-white hover:text-red-500 transition-colors z-50 p-2">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5"><path d="M6 18L18 6M6 6l12 12" /></svg>
      </button>
      <button v-if="activeProduct.images.length > 1" @click="prevImage" class="absolute left-4 text-white hover:bg-white/20 transition-colors z-50 p-3 rounded-full">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><path d="M15 19l-7-7 7-7" /></svg>
      </button>
      <div class="relative max-w-4xl max-h-[85vh] flex flex-col items-center">
        <img :src="activeProduct.images[activeImageIndex]" class="max-w-full max-h-[75vh] object-contain rounded-md shadow-2xl bg-white p-2">
        <p class="text-white mt-6 text-center font-bold text-lg px-4">{{ activeProduct.name }}</p>
        <div class="flex gap-2 mt-4" v-if="activeProduct.images.length > 1">
           <div v-for="(img, i) in activeProduct.images" :key="i" 
                class="w-2 h-2 rounded-full transition-colors"
                :class="i === activeImageIndex ? 'bg-white' : 'bg-white/30'">
           </div>
        </div>
      </div>
      <button v-if="activeProduct.images.length > 1" @click="nextImage" class="absolute right-4 text-white hover:bg-white/20 transition-colors z-50 p-3 rounded-full">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><path d="M9 5l7 7-7 7" /></svg>
      </button>
    </div>
  </div>
</template>

<style>
/* Animação para o Slider de Marcas Infinito */
@keyframes marquee {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}
.animate-marquee {
  display: flex;
  width: max-content;
  animation: marquee 30s linear infinite;
}
/* Pausa ao passar o mouse para facilitar leitura se o usuário quiser */
.animate-marquee:hover {
  animation-play-state: paused;
}
</style>