<template>
  <div
    class="bg-[#1e1e1f] px-5 py-5 md:px-12 md:py-10 text-left border border-[#383838] rounded-3xl text-amber-50 mx-3 mb-5">
    <article data-page="about">

      <!-- Titolo About -->
      <header>
        <div class="text-2xl font-bold text-white mb-5 fadein-bot title-section flex items-center">
          About Me &nbsp;
          <div class="h-[1px] w-32 bg-amber-200 md:w-96 aos-init aos-animate" data-aos="zoom-in-left"
            data-aos-duration="600"></div>
        </div>
      </header>

      <!-- Bio -->
      <section class="text-sm md:text-lg text-justify flex flex-col gap-4 md:flex-row md:gap-8 md:justify-left md:items-center">
        <div class="flex justify-center">
          <img class="w-9/12 rounded-full mb-3 fadein-up"
            src="https://i1.sndcdn.com/avatars-000214125831-5q6tdw-t500x500.jpg" alt="Foto">
        </div>
        <div class="md:w-7/12">
          <p class="mb-3 md:mb-7 fadein-left fadeins-1">
            Studente estroverso e creativo, appassionato di informatica, film e musica. Mi piace esprimermi attraverso la tecnologia e le arti digitali.
            Amo cucinare, imparare cose nuove e comunicare in modo creativo.
          </p>
          <p class="mb-3 fadein-left fadeins-2">
            Attualmente studio Informatica presso l'Università della Calabria e sono diplomato al Liceo Scientifico Galileo Galilei di Lamezia Terme.
            La mia missione è combinare tecnologia e creatività per costruire esperienze digitali significative e coinvolgenti.
          </p>
        </div>
      </section>

      <!-- Istruzione -->
      <section class="mt-10">
        <h3 class="text-xl font-semibold text-white mb-3">🎓 Istruzione</h3>
        <ul class="list-disc list-inside text-sm md:text-base">
          <li><strong>Diploma Scientifico</strong> – Liceo Scientifico Galileo Galilei, Lamezia Terme (2019 – 2024)</li>
          <li><strong>Laurea Triennale in Informatica</strong> – Università della Calabria (2024 – In corso)</li>
        </ul>
      </section>

      <!-- Interessi -->
      <section class="mt-8">
        <h3 class="text-xl font-semibold text-white mb-3">💡 Interessi</h3>
        <ul class="list-disc list-inside text-sm md:text-base">
          <li>Film e musica</li>
          <li>Informatica e tecnologia</li>
          <li>Creatività e comunicazione</li>
        </ul>
      </section>

      <!-- Skills -->
      <section class="mt-10">
        <header>
          <div class="text-2xl font-bold text-white mb-5 fadein-bot title-section flex items-center">
            <div class="h-[1px] w-10 bg-amber-200 md:w-20 aos-init aos-animate" data-aos="zoom-in-left"
              data-aos-duration="600"></div>
            &nbsp; Skills
          </div>
        </header>
        <div>
          <ul class="flex flex-wrap text-sm font-medium text-center text-gray-500 dark:text-gray-400 mb-5">
            <li class="mr-2">
              <button class="inline-block px-4 py-3 rounded-lg hover:text-white"
                :class="{ 'text-amber-200 bg-amber-200 bg-opacity-10': activeTab === 1 }" @click="activeTab = 1">Tech Stack</button>
            </li>
            <li class="mr-2">
              <button class="inline-block px-4 py-3 rounded-lg hover:text-white"
                :class="{ 'text-amber-200 bg-amber-200 bg-opacity-10': activeTab === 2 }" @click="activeTab = 2">Tools</button>
            </li>
          </ul>
        </div>

        <!-- Tech Stack -->
        <div v-show="activeTab === 1">
          <div class="grid grid-cols-2 gap-4 pb-10 md:grid-cols-3 md:gap-8 xl:grid-cols-4 xl:gap-10 2xl:gap-12">
            <div v-for="item in tech" :key="item.id">
              <div class="item-tech flex cursor-pointer items-center gap-2 rounded border border-amber-200 px-2 py-2 hover:bg-amber-200 hover:bg-opacity-10 md:gap-3 lg:px-3">
                <div class="flex h-12 w-12 items-center justify-center p-0 lg:h-16 lg:w-16 lg:p-2 zoom-in">
                  <img :src="item.imageUrl" class="img-tech drop-shadow-xl transition-all duration-300 h-[65%] w-[65%] lg:h-[85%] lg:w-[85%]" />
                </div>
                <div class="flex items-center text-sm md:text-base lg:text-lg">
                  <div class="tech font-medium text-secondary transition-all duration-300 translate-y-0">{{ item.name }}</div>
                  <div class="status-tech opacity-0 absolute mt-5 text-[10px] text-amber-200 transition-all duration-300 md:text-xs lg:text-sm">
                    {{ item.status }}
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Tools -->
        <div v-show="activeTab === 2">
          <div class="grid grid-cols-2 gap-4 pb-10 md:grid-cols-3 md:gap-8 xl:grid-cols-4 xl:gap-10 2xl:gap-12">
            <div v-for="item in tools" :key="item.id">
              <div class="item-tech flex cursor-pointer items-center gap-2 rounded border border-amber-200 px-2 py-2 hover:bg-amber-200 hover:bg-opacity-10 md:gap-3 lg:px-3">
                <div class="flex h-12 w-12 items-center justify-center p-0 lg:h-16 lg:w-16 lg:p-2 zoom-in">
                  <img :src="item.imageUrl" class="img-tech drop-shadow-xl transition-all duration-300 h-[65%] w-[65%] lg:h-[85%] lg:w-[85%]" />
                </div>
                <div class="flex items-center text-sm md:text-base lg:text-lg">
                  <div class="tech font-medium text-secondary transition-all duration-300 translate-y-0">{{ item.name }}</div>
                  <div class="status-tech opacity-0 absolute mt-5 text-[10px] text-amber-200 transition-all duration-300 md:text-xs lg:text-sm">
                    {{ item.status }}
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

      </section>
    </article>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeTab: 1,
      tech: [/* come nel tuo script */],
      tools: [/* come nel tuo script */]
    };
  }
};
</script>

<style>
/* come nel tuo style attuale, va bene */
</style>
