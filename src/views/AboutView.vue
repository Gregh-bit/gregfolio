<template>
  <div class="bg-[#1e1e1f] px-5 py-5 md:px-12 md:py-10 text-left border border-[#383838] rounded-3xl text-amber-50 mx-3 mb-5">
    <header>
      <div class="text-2xl font-bold text-white mb-5 fadein-bot title-section flex items-center">
        About Me &nbsp;
        <div class="h-[1px] w-32 bg-amber-200 md:w-96 aos-init aos-animate" data-aos="zoom-in-left" data-aos-duration="600"></div>
      </div>
    </header>

    <section class="text-sm md:text-lg text-justify flex flex-col gap-4 md:flex-row md:gap-8 md:justify-left md:items-center">
      <div class="flex justify-center">
        <img class="w-9/12 rounded-full mb-3 fadein-up" src="https://i1.sndcdn.com/avatars-000214125831-5q6tdw-t500x500.jpg" alt="Foto">
      </div>
      <div class="md:w-7/12">
        <p class="mb-3 md:mb-7 fadein-left fadeins-1">
          &nbsp; &nbsp; &nbsp; Sono uno studente estroverso e creativo, appassionato di informatica, film e musica. Amo esprimermi attraverso la tecnologia e le arti digitali. Mi piace cucinare e apprendere cose nuove ogni giorno.
        </p>
      </div>
    </section>
  </div>

  <div class="px-5 py-5 md:px-12 md:py-10 text-left text-amber-50 mx-3">
    <header>
      <div class="text-2xl font-bold text-white mb-5 fadein-bot title-section flex items-center">
        <div class="h-[1px] w-10 bg-amber-200 md:w-20 aos-init aos-animate" data-aos="zoom-in-left" data-aos-duration="600"></div>
        &nbsp; Competenze e Interessi
      </div>
    </header>

    <section>
      <ul class="flex flex-wrap text-sm font-medium text-center text-gray-500 dark:text-gray-400 mb-5">
        <li class="mr-2" v-for="tab in tabs" :key="tab.id">
          <button
            class="inline-block px-4 py-3 rounded-lg hover:text-white"
            :class="{ 'text-amber-200 bg-amber-200 bg-opacity-10': activeTab === tab.id }"
            @click="activeTab = tab.id"
          >
            {{ tab.label }}
          </button>
        </li>
      </ul>

      <div v-show="activeTab === 1">
        <SkillGrid :items="tech" />
      </div>

      <div v-show="activeTab === 2">
        <SkillGrid :items="tools" />
      </div>

      <div v-show="activeTab === 3">
        <SkillGrid :items="education" />
      </div>

      <div v-show="activeTab === 4">
        <SkillGrid :items="interests" />
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeTab: 1,
      tabs: [
        { id: 1, label: 'Tech Stack' },
        { id: 2, label: 'Strumenti' },
        { id: 3, label: 'Istruzione' },
        { id: 4, label: 'Interessi' }
      ],
      tech: [
        { id: 1, name: 'HTML', imageUrl: 'https://cdn-icons-png.flaticon.com/512/1051/1051277.png', status: 'Avanzato' },
        { id: 2, name: 'CSS', imageUrl: 'https://cdn-icons-png.flaticon.com/512/732/732190.png', status: 'Avanzato' },
        { id: 3, name: 'Javascript', imageUrl: 'https://cdn.icon-icons.com/icons2/2415/PNG/512/javascript_original_logo_icon_146455.png', status: 'Avanzato' },
        { id: 4, name: 'VueJS', imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/free-vue-282497.png?f=webp', status: 'Principiante' },
        { id: 5, name: 'Tailwind', imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/d/d5/Tailwind_CSS_Logo.svg', status: 'Principiante' },
        { id: 6, name: 'Python', imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/free-python-3521655-2945099.png', status: 'Avanzato' }
      ],
      tools: [
        { id: 1, name: 'GitHub', imageUrl: 'https://cdn-icons-png.flaticon.com/512/25/25231.png', status: 'Hosting codice' },
        { id: 2, name: 'Canva', imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/0/08/Canva_icon_2021.svg', status: 'Design grafico' },
        { id: 3, name: 'Photoshop', imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/a/af/Adobe_Photoshop_CC_icon.svg', status: 'Editing immagini' },
        { id: 4, name: 'DaVinci Resolve', imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/2/2f/DaVinci_Resolve_17_logo.svg', status: 'Montaggio video' },
        { id: 5, name: 'Microsoft Office', imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/4/4e/Microsoft_Office_Logo_%282019%E2%80%93present%29.svg', status: 'Suite produttività' }
      ],
      education: [
        { id: 1, name: 'Diploma Scientifico', imageUrl: 'https://cdn-icons-png.flaticon.com/512/3135/3135755.png', status: 'Liceo Galileo Galilei, Lamezia Terme (2019–2024)' },
        { id: 2, name: 'Laurea Triennale in Informatica', imageUrl: 'https://cdn-icons-png.flaticon.com/512/1077/1077063.png', status: 'UNICAL (2024 – in corso)' }
      ],
      interests: [
        { id: 1, name: 'Film e Musica', imageUrl: 'https://cdn-icons-png.flaticon.com/512/727/727245.png', status: 'Appassionato di cinema e ascolto musicale' },
        { id: 2, name: 'Informatica e Tecnologia', imageUrl: 'https://cdn-icons-png.flaticon.com/512/2721/2721297.png', status: 'Curioso verso software e hardware' },
        { id: 3, name: 'Creatività e Comunicazione', imageUrl: 'https://cdn-icons-png.flaticon.com/512/2942/2942927.png', status: 'Espressione personale e condivisione' }
      ]
    };
  },
  components: {
    SkillGrid: {
      props: ['items'],
      template: `
        <div class="grid grid-cols-2 gap-4 pb-32 md:grid-cols-3 md:gap-8 xl:grid-cols-4 xl:gap-10 2xl:gap-12">
          <div v-for="item in items" :key="item.id">
            <div class="item-tech flex cursor-pointer items-center gap-2 rounded border border-amber-200 px-2 py-2 hover:bg-amber-200 hover:bg-opacity-10 md:gap-3 lg:px-3">
              <div class="flex h-12 w-12 items-center justify-center p-0 lg:h-16 lg:w-16 lg:p-2 zoom-in">
                <img :src="item.imageUrl" class="img-tech drop-shadow-xl transition-all duration-300 h-[65%] w-[65%] lg:h-[85%] lg:w-[85%]" />
              </div>
              <div class="flex items-center text-sm md:text-base lg:text-lg">
                <div class="tech font-medium text-secondary transition-all duration-300 translate-y-0">{{ item.name }}</div>
                <div class="status-tech opacity-0 absolute mt-5 text-[10px] text-amber-200 transition-all duration-300 md:text-xs lg:text-sm">{{ item.status }}</div>
              </div>
            </div>
          </div>
        </div>
      `
    }
  }
};
</script>

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
  animation-delay: 0.5s;
  animation-fill-mode: both;
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
