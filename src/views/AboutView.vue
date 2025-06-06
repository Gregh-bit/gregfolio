<script>
export default {
  data() {
    return {
      activeTab: 1,
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
          status: 'Principiante'
        },
        {
          id: 3,
          name: 'Javascript',
          imageUrl: 'https://cdn.icon-icons.com/icons2/2415/PNG/512/javascript_original_logo_icon_146455.png',
          status: 'Principiante'
        },
        {
          id: 4,
          name: 'VueJS',
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
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/free-python-3521655-2945099.png',
          status: 'Avanzato'
        }
      ],
      tools: [
        {
          id: 1,
          name: 'GitHub',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/25/25231.png',
          status: 'Hosting codice'
        },
        {
          id: 2,
          name: 'Canva',
          imageUrl: 'https://cdn-1.webcatalog.io/catalog/canva-cn/canva-cn-icon-unplated.png?v=1748220584563',
          status: 'Design grafico'
        },
        {
          id: 3,
          name: 'Photoshop',
          imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/a/af/Adobe_Photoshop_CC_icon.svg',
          status: 'Editing immagini'
        },
        {
          id: 4,
          name: 'DaVinci Resolve',
          imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/4/4d/DaVinci_Resolve_Studio.png',
          status: 'Montaggio video'
        },
        {
          id: 5,
          name: 'Microsoft Office',
          imageUrl: 'https://img.icons8.com/color/512/microsoft-office-2019.png',
          status: 'Suite produttività'
        },
        {
          id: 6,
          name: 'CapCut',
          imageUrl: 'https://gpng.net/wp-content/uploads/Capcut-Logo-Transparent-PNG.png',
          status: 'Montaggio video'
        },
        {
          id: 7,
          name: 'Shopify',
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/free-shopify-logo-icon-download-in-svg-png-gif-file-formats--online-shopping-brand-logos-pack-icons-226579.png?f=webp&w=256',
          status: 'E-Commerce'
        },
        {
          id: 8,
          name: 'Wordpress',
          imageUrl: 'https://static-00.iconduck.com/assets.00/wordpress-icon-2048x2048-nw66awj8.png',
          status: 'Web Developer'
        }
      ],
      education: [
        {
          id: 1,
          name: 'Diploma Scientifico',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/4466/4466436.png',
          status: 'Liceo Galilei 2019 – 2024'
        },
        {
          id: 2,
          name: 'Laurea in Informatica',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/8824/8824175.png',
          status: 'UNICAL 2024 – in corso'
        }
      ],
      interests: [
        {
          id: 1,
          name: 'Film e Musica',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/727/727245.png',
          status: 'Cinema, Videomaking'
        },
        {
          id: 2,
          name: 'Tecnologia',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/6985/6985378.png',
          status: 'Hardware e Software'
        },
        {
          id: 3,
          name: 'Creatività',
          imageUrl: 'https://cdn-icons-png.freepik.com/256/15557/15557915.png',
          status: 'Creator'
        }
      ],
      indicatorStyle: {
        width: '0px',
        left: '0px'
      }
    };
  },
  mounted() {
    this.$nextTick(() => {
      // Inizializza indicatore sul tab attivo al montaggio
      const el = this.$refs[`tab-${this.activeTab}`][0];
      if (el) this.setIndicator(el);
    });
  },
  methods: {
    setIndicator(el) {
      this.indicatorStyle = {
        width: el.offsetWidth + 'px',
        left: el.offsetLeft + 'px'
      };
    },
    selectTab(id) {
      this.activeTab = id;
      this.$nextTick(() => {
        const el = this.$refs[`tab-${id}`][0];
        if (el) this.setIndicator(el);
      });
    }
  }
};
</script>

<template>
  <div class="bg-[#1e1e1f] px-5 py-5 md:px-12 md:py-10 text-left border border-[#383838] rounded-3xl text-amber-50 mx-3 mb-5">
    <article data-page="about">
      <header>
        <div class="text-2xl font-bold text-white mb-5 fadein-bot title-section flex items-center">
          About Me &nbsp;
          <div class="h-[1px] w-32 bg-amber-200 md:w-96 aos-init aos-animate" data-aos="zoom-in-left" data-aos-duration="600"></div>
        </div>
      </header>

      <section class="text-sm md:text-lg text-justify flex flex-col gap-4 md:flex-row md:gap-8 md:justify-left md:items-center">
        <div class="flex justify-center">
          <img class="w-9/12 rounded-full mb-3 fadein-up" src="https://i1.sndcdn.com/avatars-000214125831-5q6tdw-t500x500.jpg" alt="Foto" />
        </div>
        <div class="md:w-7/12">
          <p class="mb-3 md:mb-7 fadein-left fadeins-1">
            &nbsp; &nbsp; &nbsp; Sono uno studente estroverso e creativo, appassionato di informatica, film e musica. Amo esprimermi attraverso la tecnologia e le arti digitali. Mi piace cucinare e apprendere cose nuove ogni giorno.
          </p>
        </div>
      </section>
    </article>
  </div>

  <div class="px-5 py-5 md:px-12 md:py-10 text-left text-amber-50 mx-3">
    <article data-page="about">
      <header>
        <div class="text-2xl font-bold text-white mb-5 fadein-bot title-section flex items-center">
          <div class="h-[1px] w-10 bg-amber-200 md:w-20 aos-init aos-animate" data-aos="zoom-in-left" data-aos-duration="600"></div>
          &nbsp; Competenze e Interessi
        </div>
      </header>
      <section>
        <nav class="relative border-b border-gray-600 mb-5">
          <ul class="flex space-x-4">
            <li>
              <button
                ref="tab-1"
                @click="selectTab(1)"
                :class="['relative py-3 font-semibold', activeTab === 1 ? 'text-amber-200' : 'text-gray-400 hover:text-amber-400']"
              >
                Tech Stack
              </button>
            </li>
            <li>
              <button
                ref="tab-2"
                @click="selectTab(2)"
                :class="['relative py-3 font-semibold', activeTab === 2 ? 'text-amber-200' : 'text-gray-400 hover:text-amber-400']"
              >
                Strumenti
              </button>
            </li>
            <li>
              <button
                ref="tab-3"
                @click="selectTab(3)"
                :class="['relative py-3 font-semibold', activeTab === 3 ? 'text-amber-200' : 'text-gray-400 hover:text-amber-400']"
              >
                Istruzione
              </button>
            </li>
            <li>
              <button
                ref="tab-4"
                @click="selectTab(4)"
                :class="['relative py-3 font-semibold', activeTab === 4 ? 'text-amber-200' : 'text-gray-400 hover:text-amber-400']"
              >
                Interessi
              </button>
            </li>
          </ul>
          <!-- Indicatore animato -->
          <div
            class="absolute bottom-0 h-1 bg-amber-200 rounded transition-all duration-300"
            :style="{ width: indicatorStyle.width, left: indicatorStyle.left }"
          ></div>
        </nav>

        <div v-show="activeTab === 1" class="grid grid-cols-3 md:grid-cols-6 gap-5 mb-5 fadein-up fadeins-1">
          <div v-for="item in tech" :key="item.id" class="flex flex-col items-center justify-center gap-2">
            <img :src="item.imageUrl" :alt="item.name" class="w-12 h-12" />
            <p class="text-xs text-amber-200 text-center">{{ item.name }}</p>
            <p class="text-xs text-gray-400 text-center">{{ item.status }}</p>
          </div>
        </div>

        <div v-show="activeTab === 2" class="grid grid-cols-3 md:grid-cols-6 gap-5 mb-5 fadein-up fadeins-1">
          <div v-for="item in tools" :key="item.id" class="flex flex-col items-center justify-center gap-2">
            <img :src="item.imageUrl" :alt="item.name" class="w-12 h-12" />
            <p class="text-xs text-amber-200 text-center">{{ item.name }}</p>
            <p class="text-xs text-gray-400 text-center">{{ item.status }}</p>
          </div>
        </div>

        <div v-show="activeTab === 3" class="grid grid-cols-1 md:grid-cols-2 gap-5 mb-5 fadein-up fadeins-1">
          <div v-for="item in education" :key="item.id" class="flex items-center gap-4">
            <img :src="item.imageUrl" :alt="item.name" class="w-12 h-12" />
            <div>
              <p class="text-base font-semibold text-amber-200">{{ item.name }}</p>
              <p class="text-xs text-gray-400">{{ item.status }}</p>
            </div>
          </div>
        </div>

        <div v-show="activeTab === 4" class="grid grid-cols-1 md:grid-cols-3 gap-5 mb-5 fadein-up fadeins-1">
          <div v-for="item in interests" :key="item.id" class="flex flex-col items-center gap-2">
            <img :src="item.imageUrl" :alt="item.name" class="w-12 h-12" />
            <p class="text-base font-semibold text-amber-200">{{ item.name }}</p>
            <p class="text-xs text-gray-400 text-center">{{ item.status }}</p>
          </div>
        </div>
      </section>
    </article>
  </div>
</template>

<style scoped>
/* puoi aggiungere stili personalizzati se vuoi */
</style>
