<script setup>
import { ref } from 'vue'

// Configurações do WhatsApp
const whatsappNumber = "5511999999999" // Coloque seu número aqui
const defaultMessage = "Olá! Vim do site Central dos Assentos e gostaria de enviar a foto do meu vaso sanitário para vocês confirmarem o modelo exato para mim."
const waLink = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(defaultMessage)}`

// Produtos REAIS extraídos da sua loja
const topSellers = ref([
  {
    id: 1,
    name: 'Assento Acrílico Transparente Thema (Incepa)',
    description: 'Resina poliéster virgem, ferragem reforçada e batentes em PVC flexível. Design incolor elegante.',
    price: 'R$ 276,20',
    image: 'https://via.placeholder.com/400x400/ffffff/1E3A8A?text=Thema+Transparente', 
    paymentLink: '#'
  },
  {
    id: 2,
    name: 'Assento Decorado Borboleta Resina Incolor (Oval)',
    description: 'Peça artesanal exclusiva. As borboletas dão um toque único. Compatível com Deca, Icasa e Celite.',
    price: 'R$ 251,09',
    image: 'https://via.placeholder.com/400x400/ffffff/1E3A8A?text=Borboleta+Incolor',
    paymentLink: '#'
  },
  {
    id: 3,
    name: 'Assento Quadrado Bali Preto (Incepa)',
    description: 'Modelo quadrado específico para Incepa Bali. Dobradiças em aço garantem total segurança e estabilidade.',
    price: 'R$ 269,00', 
    image: 'https://via.placeholder.com/400x400/ffffff/1E3A8A?text=Bali+Preto',
    paymentLink: '#'
  },
  {
    id: 4,
    name: 'Assento Convencional Liso c/ Glitter Branco',
    description: 'Acabamento brilhante e alta durabilidade para vasos ovais. Renova o ambiente com muita sofisticação.',
    price: 'R$ 189,90', 
    image: 'https://via.placeholder.com/400x400/ffffff/1E3A8A?text=Glitter+Branco',
    paymentLink: '#'
  },
  {
    id: 5,
    name: 'Assento Decorado Mármore Ouro Dourado',
    description: 'Sofisticação máxima com textura marmorizada artesanal. Transforma o visual do banheiro.',
    price: 'R$ 299,00',
    image: 'https://via.placeholder.com/400x400/ffffff/1E3A8A?text=Marmore+Ouro',
    paymentLink: '#'
  },
  {
    id: 6,
    name: 'Assento Fit Celite Golfinho Areia Azul',
    description: 'Design temático de fundo do mar com areia e golfinhos. Resina de altíssima qualidade e resistência.',
    price: 'R$ 289,00',
    image: 'https://via.placeholder.com/400x400/ffffff/1E3A8A?text=Golfinho+Areia',
    paymentLink: '#'
  }
])
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
          <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 fill-current" viewBox="0 0 24 24">
            <path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.582 2.128 2.182-.573c.978.58 1.911.928 3.145.929 3.178 0 5.767-2.587 5.768-5.766.001-3.187-2.575-5.77-5.764-5.771zm3.392 8.244c-.144.405-.837.774-1.17.824-.299.045-.677.063-1.092-.125-.397-.179-.974-.396-1.76-1.18-.783-.78-1.291-1.637-1.488-1.996-.197-.36-.021-.555.158-.733.161-.16.353-.414.53-.62.176-.206.236-.353.353-.588.118-.235.059-.441-.029-.618-.088-.176-.783-1.888-1.071-2.584-.282-.678-.567-.585-.773-.596-.197-.01-.423-.01-.649-.01-.225 0-.589.084-.897.418-.308.334-1.176 1.147-1.176 2.793s1.205 3.235 1.373 3.46c.167.225 2.36 3.593 5.713 5.039 2.261.974 3.033.856 3.555.733.522-.123 1.685-.688 1.921-1.353.236-.665.236-1.235.167-1.353-.069-.118-.285-.186-.62-.353z"/>
          </svg>
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

          <div class="overflow-hidden">
             <img :src="product.image" :alt="product.name" class="w-full h-72 object-cover object-center bg-gray-200 group-hover:scale-105 transition-transform duration-300">
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

    <a :href="waLink" target="_blank" class="fixed bottom-6 right-6 bg-green-500 text-white p-4 rounded-full shadow-2xl hover:bg-green-600 hover:scale-110 transition-transform z-50 flex items-center justify-center">
      <svg xmlns="http://www.w3.org/2000/svg" class="w-8 h-8 fill-current" viewBox="0 0 24 24">
        <path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.582 2.128 2.182-.573c.978.58 1.911.928 3.145.929 3.178 0 5.767-2.587 5.768-5.766.001-3.187-2.575-5.77-5.764-5.771zm3.392 8.244c-.144.405-.837.774-1.17.824-.299.045-.677.063-1.092-.125-.397-.179-.974-.396-1.76-1.18-.783-.78-1.291-1.637-1.488-1.996-.197-.36-.021-.555.158-.733.161-.16.353-.414.53-.62.176-.206.236-.353.353-.588.118-.235.059-.441-.029-.618-.088-.176-.783-1.888-1.071-2.584-.282-.678-.567-.585-.773-.596-.197-.01-.423-.01-.649-.01-.225 0-.589.084-.897.418-.308.334-1.176 1.147-1.176 2.793s1.205 3.235 1.373 3.46c.167.225 2.36 3.593 5.713 5.039 2.261.974 3.033.856 3.555.733.522-.123 1.685-.688 1.921-1.353.236-.665.236-1.235.167-1.353-.069-.118-.285-.186-.62-.353z"/>
      </svg>
    </a>

    <footer class="bg-gray-900 text-gray-400 text-center py-8">
      <p>&copy; 2026 Central dos Assentos. Todos os direitos reservados.</p>
    </footer>
    
  </div>
</template>