<script setup>
import { Motion } from 'motion-v'
</script>

<script>
import SmoothTabs from 'src/components/SmoothTabs.vue'

export default {
  components: {
    SmoothTabs
  },
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
      ]
    }
  }
}
</script>

<template>
  <!-- Sezione Chi sono (Motion) -->
  <Motion
    :initial="{ opacity: 0, y: 50 }"
    :enter="{ opacity: 1, y: 0 }"
    transition="ease-in-out"
    class="min-h-screen flex items-center justify-center py-10"
  >
    <div class="text-center max-w-4xl mx-auto px-4">
      <h1 class="text-4xl md:text-5xl font-bold mb-6 text-white">Chi sono</h1>
      <p class="text-gray-300 mb-6">
        Sono uno studente appassionato di tecnologia, design e sviluppo web. Amo combinare creatività e logica per costruire progetti intuitivi ed efficienti.
      </p>

      <div class="grid md:grid-cols-2 gap-8 text-left text-gray-200">
        <div>
          <h2 class="text-xl font-semibold mb-2 text-white">🎓 Istruzione</h2>
          <ul class="list-disc list-inside text-gray-300">
            <li>Diploma di scuola superiore</li>
            <li>Studi universitari in corso</li>
          </ul>
        </div>
        <div>
          <h2 class="text-xl font-semibold mb-2 text-white">🎯 Interessi</h2>
          <ul class="list-disc list-inside text-gray-300">
            <li>Sviluppo front-end</li>
            <li>UI/UX design</li>
            <li>Montaggio video e creatività digitale</li>
          </ul>
        </div>
      </div>
    </div>
  </Motion>

  <!-- Sezione Competenze e Interessi -->
  <div class="px-5 py-5 md:px-12 md:py-10 text-left text-amber-50 mx-3">
    <article data-page="about">
      <header>
        <div class="text-2xl font-bold text-white mb-5 fadein-bot title-section flex items-center">
          <div class="h-[1px] w-10 bg-amber-200 md:w-20 aos-init aos-animate" data-aos="zoom-in-left" data-aos-duration="600"></div>
          &nbsp; Competenze e Interessi
        </div>
      </header>
      <SmoothTabs :tech="tech" :tools="tools" :education="education" :interests="interests" />
    </article>
  </div>
</template>

<style>
.fadein-left {
  opacity: 0;
  animation: fadeInLeft 0.5s ease-out forwards;
}
@keyframes fadeInLeft {
  0% {
    opacity: 0;
    transform: translateX(100%);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}
.fadeins-1 {
  animation-delay: 500ms;
}
.img-tech,
.tech {
  transition: transform 0.3s ease;
}
.item-tech:hover .img-tech {
  transform: scale(1.3);
}
.item-tech:hover .tech {
  transform: translateY(-12px);
}
.item-tech:hover .status-tech {
  opacity: 1;
}
</style>
