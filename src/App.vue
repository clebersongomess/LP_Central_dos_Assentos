<script setup>
import { ref } from 'vue'

const whatsappNumber = "5511945785565" // Coloque seu número aqui
const defaultMessage = "Olá! Vim do site Central dos Assentos e gostaria de enviar a foto do meu vaso sanitário para vocês confirmarem o modelo exato para mim."
const waLink = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(defaultMessage)}`

// Agora cada produto tem um Array (lista) de imagens
const topSellers = ref([
  {
    id: 1,
    name: 'Assento Acrílico Transparente Thema (Incepa)',
    description: 'Resina poliéster virgem, ferragem reforçada e batentes em PVC flexível. Design incolor elegante.',
    price: 'R$ 276,20',
    // Coloque as fotos desse produto aqui (ex: foto de frente, de lado, detalhe da dobradiça)
    images: [
      '/thema-1.png', 
      '/thema-2.png',
      '/thema-3.png'
    ], 
    paymentLink: 'https://mpago.la/2M8YXe6'
  },
  {
    id: 2,
    name: 'Assento Decorado Borboleta Resina Incolor (Oval)',
    description: 'Peça artesanal exclusiva. As borboletas dão um toque único. Compatível com Deca, Icasa e Celite.',
    price: 'R$ 251,09',
    images: [
      '/thema-1.png', 
      '/thema-2.png',
      '/thema-3.png'
    ],
    paymentLink: 'https://mpago.la/1MnJcxZ'
  },
  {
    id: 3,
    name: 'Assento Quadrado Bali Preto (Incepa)',
    description: 'Modelo quadrado específico para Incepa Bali. Dobradiças em aço garantem total segurança e estabilidade.',
    price: 'R$ 269,00', 
    images: [
      '/thema-1.png', 
      '/thema-2.png',
      '/thema-3.png'
    ],
    paymentLink: 'https://mpago.la/2iRiAKm'
  },
  {
    id: 4,
    name: 'Assento Convencional Liso c/ Glitter Branco',
    description: 'Acabamento brilhante e alta durabilidade para vasos ovais. Renova o ambiente com muita sofisticação.',
    price: 'R$ 189,90', 
    images: [
      '/thema-1.png', 
      '/thema-2.png',
      '/thema-3.png'
    ],
    paymentLink: 'https://mpago.la/1T8bxPb'
  },
  {
    id: 5,
    name: 'Assento Decorado Mármore Ouro Dourado',
    description: 'Sofisticação máxima com textura marmorizada artesanal. Transforma o visual do banheiro.',
    price: 'R$ 299,00',
    images: [
      '/thema-1.png', 
      '/thema-2.png',
      '/thema-3.png'
    ],
    paymentLink: 'https://mpago.la/1vetgAN'
  },
  {
    id: 6,
    name: 'Assento Fit Celite Golfinho Areia Azul',
    description: 'Design temático de fundo do mar com areia e golfinhos. Resina de altíssima qualidade e resistência.',
    price: 'R$ 289,00',
    images: [
      '/thema-1.png', 
      '/thema-2.png',
      '/thema-3.png'
    ],
    paymentLink: 'https://mpago.la/1ewGUrY'
  }
])

// ESTADO DA GALERIA (LIGHTBOX)
const isGalleryOpen = ref(false)
const activeProduct = ref(null)
const activeImageIndex = ref(0)

// Funções para controlar a galeria
const openGallery = (product) => {
  activeProduct.value = product
  activeImageIndex.value = 0
  isGalleryOpen.value = true
  document.body.style.overflow = 'hidden' // Trava o scroll da página no fundo
}

const closeGallery = () => {
  isGalleryOpen.value = false
  activeProduct.value = null
  document.body.style.overflow = 'auto' // Destrava o scroll
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
    
    <div class="bg-green-600 text-white text-center py-2 px-4 text-sm font-bold tracking-wide shadow-sm flex items-center justify-center gap-2">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
        <path d="M8 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0zM15 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0z" />
        <path d="M3 4a1 1 0 00-1 1v10a1 1 0 001 1h1.05a2.5 2.5 0 014.9 0H10a1 1 0 001-1V5a1 1 0 00-1-1H3zM14 7a1 1 0 00-1 1v6.05A2.5 2.5 0 0115.95 16H17a1 1 0 001-1v-5a1 1 0 00-.293-.707l-2-2A1 1 0 0015 7h-1z" />
      </svg>
      PROMOÇÃO: Frete Grátis para todo o Estado de São Paulo!
    </div>

    <header class="bg-blue-900 text-white text-center py-16 px-4">
      <h1 class="text-4xl md:text-5xl font-bold mb-4 tracking-tight">Central dos Assentos</h1>
      <p class="text-lg md:text-xl text-blue-200 max-w-2xl mx-auto mb-8">
        O fim da dor de cabeça na hora de trocar a tampa da privada. Peças de fábrica em resina poliéster virgem com o encaixe perfeito para o seu vaso.
      </p>
      
      <div class="bg-blue-800/50 p-6 rounded-xl max-w-3xl mx-auto border border-blue-700 mb-8">
        <h3 class="text-xl font-bold text-yellow-400 mb-2">Não sabe qual é o seu modelo?</h3>
        <p class="text-blue-100 mb-4">A maioria das tampas não são universais. Envie uma foto do seu vaso sanitário para nós e indicamos a peça exata na hora!</p>
        <a :href="waLink" target="_blank" class="bg-green-500 hover:bg-green-600 transition-colors text-white font-bold py-3 px-6 rounded-lg shadow-lg flex items-center justify-center w-fit mx-auto gap-2">
          <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 fill-current" viewBox="0 0 24 24"><path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.582 2.128 2.182-.573c.978.58 1.911.928 3.145.929 3.178 0 5.767-2.587 5.768-5.766.001-3.187-2.575-5.77-5.764-5.771zm3.392 8.244c-.144.405-.837.774-1.17.824-.299.045-.677.063-1.092-.125-.397-.179-.974-.396-1.76-1.18-.783-.78-1.291-1.637-1.488-1.996-.197-.36-.021-.555.158-.733.161-.16.353-.414.53-.62.176-.206.236-.353.353-.588.118-.235.059-.441-.029-.618-.088-.176-.783-1.888-1.071-2.584-.282-.678-.567-.585-.773-.596-.197-.01-.423-.01-.649-.01-.225 0-.589.084-.897.418-.308.334-1.176 1.147-1.176 2.793s1.205 3.235 1.373 3.46c.167.225 2.36 3.593 5.713 5.039 2.261.974 3.033.856 3.555.733.522-.123 1.685-.688 1.921-1.353.236-.665.236-1.235.167-1.353-.069-.118-.285-.186-.62-.353z"/></svg>
          Enviar foto do vaso no WhatsApp
        </a>
      </div>
    </header>

    <main class="max-w-7xl mx-auto py-16 px-4">
      <h2 class="text-3xl font-bold text-center text-gray-800 mb-2">Fabricação Própria</h2>
      <p class="text-center text-gray-500 mb-10">Os modelos de resina e acrílico mais vendidos do Brasil</p>
      
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div v-for="product in topSellers" :key="product.id" class="bg-white rounded-xl shadow-md overflow-hidden hover:shadow-xl transition-shadow border border-gray-100 flex flex-col group relative">
          
          <span class="absolute top-4 left-4 bg-green-500 text-white text-xs font-extrabold uppercase tracking-wider px-3 py-1.5 rounded-full shadow-md z-10 flex items-center gap-1">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" viewBox="0 0 20 20" fill="currentColor">
              <path d="M8 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0zM15 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0z" />
              <path d="M3 4a1 1 0 00-1 1v10a1 1 0 001 1h1.05a2.5 2.5 0 014.9 0H10a1 1 0 001-1V5a1 1 0 00-1-1H3zM14 7a1 1 0 00-1 1v6.05A2.5 2.5 0 0115.95 16H17a1 1 0 001-1v-5a1 1 0 00-.293-.707l-2-2A1 1 0 0015 7h-1z" />
            </svg>
            Frete Grátis
          </span>

          <div 
            class="overflow-hidden relative cursor-pointer"
            @click="openGallery(product)"
            title="Clique para ver mais fotos"
          >
             <img :src="product.images[0]" :alt="product.name" class="w-full h-72 object-cover object-center bg-gray-200 group-hover:scale-105 transition-transform duration-300">
             
             <div class="absolute inset-0 bg-blue-900/0 group-hover:bg-blue-900/20 transition-colors duration-300 flex items-center justify-center">
               <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12 text-white opacity-0 group-hover:opacity-100 transition-opacity duration-300 drop-shadow-lg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0zM10 7v3m0 0v3m0-3h3m-3 0H7" />
                </svg>
             </div>
          </div>
          
          <div class="p-6 flex flex-col flex-grow">
            <h3 class="text-xl font-bold text-gray-800 mb-2 leading-tight">{{ product.name }}</h3>
            <p class="text-gray-600 text-sm mb-6 flex-grow">{{ product.description }}</p>
            <div class="mt-auto border-t border-gray-100 pt-4">
              <span class="block text-3xl font-extrabold text-blue-900 mb-4">{{ product.price }}</span>
              <a :href="product.paymentLink" class="block w-full text-center bg-blue-600 hover:bg-blue-700 text-white font-bold py-3.5 rounded-lg transition-colors shadow-md">
                Comprar Agora
              </a>
            </div>
          </div>
        </div>
      </div>
    </main>

    <section class="bg-white py-12 border-t border-gray-200">
      <div class="max-w-6xl mx-auto px-4 grid grid-cols-1 md:grid-cols-3 gap-6 text-center">
        <div class="p-4">
          <div class="w-12 h-12 bg-blue-100 text-blue-600 rounded-full flex items-center justify-center mx-auto mb-4 font-bold text-xl">✓</div>
          <h4 class="font-bold text-gray-800">Ferragem Reforçada</h4>
          <p class="text-sm text-gray-500 mt-2">Maior durabilidade e estabilidade.</p>
        </div>
        <div class="p-4">
          <div class="w-12 h-12 bg-blue-100 text-blue-600 rounded-full flex items-center justify-center mx-auto mb-4 font-bold text-xl">★</div>
          <h4 class="font-bold text-gray-800">Resina Virgem</h4>
          <p class="text-sm text-gray-500 mt-2">Acabamento premium artesanal.</p>
        </div>
        <div class="p-4">
          <div class="w-12 h-12 bg-blue-100 text-blue-600 rounded-full flex items-center justify-center mx-auto mb-4 font-bold text-xl">🛡️</div>
          <h4 class="font-bold text-gray-800">Compra Garantida</h4>
          <p class="text-sm text-gray-500 mt-2">Garantia total contra defeitos de fabricação.</p>
        </div>
      </div>
    </section>

    <footer class="bg-gray-900 text-gray-400 text-center py-8">
      <p>&copy; 2026 Central dos Assentos. Todos os direitos reservados.<br />Um empresa do grupo CAG Assentos Sanitários.</p>
    </footer>

    <div 
      v-if="isGalleryOpen && activeProduct" 
      class="fixed inset-0 z-[100] flex items-center justify-center bg-black/95 backdrop-blur-sm p-4"
    >
      <button @click="closeGallery" class="absolute top-6 right-6 text-white hover:text-red-500 transition-colors z-50">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
          <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>

      <button v-if="activeProduct.images.length > 1" @click="prevImage" class="absolute left-4 md:left-10 text-white/70 hover:text-white transition-colors z-50 bg-black/50 p-2 rounded-full">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 md:h-12 md:w-12" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
          <path stroke-linecap="round" stroke-linejoin="round" d="M15 19l-7-7 7-7" />
        </svg>
      </button>

      <div class="relative max-w-4xl max-h-[85vh] flex flex-col items-center">
        <img 
          :src="activeProduct.images[activeImageIndex]" 
          :alt="activeProduct.name" 
          class="max-w-full max-h-[75vh] object-contain rounded-md shadow-2xl select-none"
        >
        <p class="text-white mt-4 text-center font-semibold text-lg">{{ activeProduct.name }}</p>
        <p v-if="activeProduct.images.length > 1" class="text-gray-400 text-sm mt-1">
          Foto {{ activeImageIndex + 1 }} de {{ activeProduct.images.length }}
        </p>
      </div>

      <button v-if="activeProduct.images.length > 1" @click="nextImage" class="absolute right-4 md:right-10 text-white/70 hover:text-white transition-colors z-50 bg-black/50 p-2 rounded-full">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 md:h-12 md:w-12" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
          <path stroke-linecap="round" stroke-linejoin="round" d="M9 5l7 7-7 7" />
        </svg>
      </button>
    </div>
    
  </div>
</template>