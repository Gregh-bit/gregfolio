<template>
  <section class="p-8">
    <div class="text-white text-center mb-10">
      <h2 class="text-4xl font-bold mb-4">Chi sono</h2>
      <p class="text-lg max-w-2xl mx-auto">
        Sono uno studente creativo ed estroverso con una forte passione per l'informatica, il cinema e la musica. Mi piace esprimermi attraverso la tecnologia e le arti digitali, oltre che cucinare e imparare continuamente cose nuove.
      </p>
    </div>

    <!-- Tech Stack -->
    <div class="mb-16">
      <h3 class="text-2xl font-semibold text-white mb-4">🧠 Competenze e Interessi</h3>
      <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
        <div v-for="item in tech" :key="item.id" class="bg-yellow-400 p-4 rounded-lg text-center hover:scale-105 transition">
          <img :src="item.imageUrl" alt="" class="h-12 mx-auto mb-2" />
          <h4 class="font-semibold">{{ item.name }}</h4>
          <p class="text-sm text-gray-800">{{ item.status }}</p>
        </div>
      </div>
    </div>

    <!-- Tools -->
    <div class="mb-16">
      <h3 class="text-2xl font-semibold text-white mb-4">🛠️ Strumenti</h3>
      <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
        <div v-for="item in tools" :key="item.id" class="bg-yellow-400 p-4 rounded-lg text-center hover:scale-105 transition">
          <img :src="item.imageUrl" alt="" class="h-12 mx-auto mb-2" />
          <h4 class="font-semibold">{{ item.name }}</h4>
          <p class="text-sm text-gray-800">{{ item.status }}</p>
        </div>
      </div>
    </div>

    <!-- Education -->
    <div class="mb-16">
      <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
        <div v-for="item in education" :key="item.id" class="bg-yellow-400 p-4 rounded-lg text-center hover:scale-105 transition group relative cursor-pointer">
          <img :src="item.imageUrl" alt="" class="h-12 mx-auto mb-2" />
          <h4 class="font-semibold">{{ item.name }}</h4>
          <div class="absolute bottom-0 left-0 right-0 bg-black bg-opacity-80 text-white text-xs p-2 opacity-0 group-hover:opacity-100 transition duration-300">
            {{ item.status }}
          </div>
        </div>
      </div>
    </div>

    <!-- Interests -->
    <div class="mb-16">
      <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
        <div v-for="item in interests" :key="item.id" class="bg-yellow-400 p-4 rounded-lg text-center hover:scale-105 transition group relative cursor-pointer">
          <img :src="item.imageUrl" alt="" class="h-12 mx-auto mb-2" />
          <h4 class="font-semibold">{{ item.name }}</h4>
          <div class="absolute bottom-0 left-0 right-0 bg-black bg-opacity-80 text-white text-xs p-2 opacity-0 group-hover:opacity-100 transition duration-300">
            {{ item.status }}
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      tech: [
        {
          id: 1,
          name: 'HTML',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/1051/1051277.png',
          status: 'Avanzato'
        },
        {
          id: 2,
          name: 'CSS',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/732/732190.png',
          status: 'Avanzato'
        },
        {
          id: 3,
          name: 'JavaScript',
          imageUrl: 'https://cdn.icon-icons.com/icons2/2415/PNG/512/javascript_original_logo_icon_146455.png',
          status: 'Avanzato'
        },
        {
          id: 4,
          name: 'Vue.js',
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/free-vue-282497.png?f=webp',
          status: 'Principiante'
        },
        {
          id: 5,
          name: 'Tailwind',
          imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/d/d5/Tailwind_CSS_Logo.svg',
          status: 'Principiante'
        },
        {
          id: 6,
          name: 'Python',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/5968/5968350.png',
          status: 'Avanzato'
        },
      ],
      tools: [
        {
          id: 1,
          name: 'GitHub',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/25/25231.png',
          status: 'Gestione codice'
        },
        {
          id: 2,
          name: 'Canva',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/5968/5968520.png',
          status: 'Grafica e design'
        },
        {
          id: 3,
          name: 'Photoshop',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/5968/5968520.png',
          status: 'Editing immagini'
        },
        {
          id: 4,
          name: 'DaVinci Resolve',
          imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/5/5a/DaVinci_Resolve_17_logo.svg',
          status: 'Montaggio video'
        },
        {
          id: 5,
          name: 'Microsoft Office',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/732/732221.png',
          status: 'Produttività'
        },
      ],
      education: [
        {
          id: 1,
          name: 'Diploma Scientifico',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/2991/2991148.png',
          status: 'Liceo Scientifico Galileo Galilei, Lamezia Terme (2019 – 2024)'
        },
        {
          id: 2,
          name: 'Laurea in Informatica',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/2991/2991148.png',
          status: 'Università della Calabria (UNICAL) – In corso dal 2024'
        }
      ],
      interests: [
        {
          id: 1,
          name: 'Film e musica',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/727/727245.png',
          status: 'Mi appassionano da sempre, rappresentano una grande fonte di ispirazione'
        },
        {
          id: 2,
          name: 'Cucina',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/1046/1046857.png',
          status: 'Mi piace sperimentare e cucinare piatti nuovi'
        },
        {
          id: 3,
          name: 'Tecnologia',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/2784/2784445.png',
          status: 'Amo scoprire e utilizzare nuovi strumenti digitali'
        },
        {
          id: 4,
          name: 'Comunicazione creativa',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/3602/3602123.png',
          status: 'Mi esprimo attraverso linguaggi visivi e digitali'
        },
      ]
    };
  }
};
</script>
