<template>
  <div
    class="my-10 text-gray-800 dark:text-gray-300"
    v-if="word.length === 0 ? false : true"
  >
    <div class="flex items-center justify-between">
      <div class="">
        <h1 class="font-bold text-4xl">{{ word.word }}</h1>
        <p class="italic text-purple-500">{{ word.phonetic }}</p>
      </div>
      <div class="">
        <div
          class="bg-purple-200 w-14 h-14 rounded-full items-center flex justify-center cursor-pointer"
          @click="playAudio"
        >
          <i class="bx bx-play text-purple-500 text-4xl"></i>
        </div>
        <p
          v-if="getSound.length === 0 ? true : false"
          class="text-red-400 text-lg"
        >
          No Sound
        </p>
      </div>
    </div>
    <div class="nouns" v-for="(item, i) in word.meanings" :key="i">
      <div class="my-10 flex items-center gap-4">
        <h3 class="font-bold text-4xl italic">{{ item.partOfSpeech }}</h3>
        <div class="w-full border border-1 items-center"></div>
      </div>
      <div class="font-medium">
        <h2 class="text-2xl text-slate-500 mb-5">Meaning</h2>
        <ul
          class="marker:text-purple-500 px-5 list-disc pl-12"
          v-for="(def, i) in item.definitions"
          :key="i"
        >
          <li class="text-lg pt-3">
            <p class="text-xl">{{ def.definition }}</p>

            <p class="text-slate-500 pt-2 italic" v-if="def.example">
              <i class="bx bxs-quote-alt-left text-sm"></i>{{ def.example }}
              <i class="bx bxs-quote-alt-right text-sm"></i>
            </p>
          </li>
        </ul>
      </div>
      <div class="font-medium md:flex items-center gap-6 mt-8">
        <h2 class="text-2xl text-slate-500">Synonyms</h2>
        <div class="">
          <span
            class="text-purple-800 font-bold text-xl inline-block mx-3"
            v-for="(syn, i) in item.synonyms"
            :key="i"
          >
            {{ syn || "" }}
          </span>
        </div>
      </div>
    </div>
    <hr class="text-slate-500 mt-4" />
    <div class="font-medium md:flex items-center gap-6 mt-4">
      <p class="text-slate-500">source</p>
      <a :href="word.sourceUrls[0]" target="_blank" class="underline">{{
        word.sourceUrls[0]
      }}</a>
    </div>
  </div>
</template>

<script>
export default {
  props: ["word"],
  data() {
    return {
      isChecked: false,
      // fetchData: [this.word],
    };
  },
  computed: {
    getSound() {
      let audios = [];
      this.word.phonetics.forEach((audio) => {
        if (audio.audio) audios.push(audio.audio);
      });
      return audios;
    },
    // getMeaning() {
    //   let meanings
    //   this.word.meanings.forEach(item =>{
    //     partOfSpeech.push(item.partOfSpeech)

    //   })
    // },
  },
  methods: {
    playAudio() {
      if (this.getSound.length === 0) return;
      new Audio(this.getSound[0]).play();
    },
  },
};
</script>

<style></style>
