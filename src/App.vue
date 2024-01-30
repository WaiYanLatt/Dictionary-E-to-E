<script>
import FormInput from "./components/FormInput.vue";
import DefinationCard from "./components/DefinationCard.vue";

export default {
  data() {
    return {
      definitions: [],
      loading: false,
    };
  },
  components: {
    FormInput,
    DefinationCard,
  },
  methods: {
    async getDefination(searchQuery) {
      this.loading = true;
      this.definitions = [];
      this.$refs.formInput.$data.searchQuery = '';
      try {
        const options = {
          method: 'GET',
          headers: {
            'X-RapidAPI-Key': '6bcaeeeda0msh5ceace7d8923e3dp163960jsna589cd53b78f',
            'X-RapidAPI-Host': 'mashape-community-urban-dictionary.p.rapidapi.com'
          }
        };
        const response = await fetch('https://mashape-community-urban-dictionary.p.rapidapi.com/define?term=' + searchQuery, options)
        const json = await response.json();

        this.definitions = json.list;

      } catch (error) {
        console.log(error);
        alert('Someting Is Worng')
      } finally {
        this.loading = false;
      }
    }


  }
};
</script>

<template>
  <div>
    <div class="container mx-auto lg:px-64 px-5 my-28">
      <h1 class="font-semibold my-10 text-xl">
        Dictionary <span class="text-rose-600">English</span> To
        <span class="text-rose-600">English</span>
      </h1>
      <FormInput ref="formInput" @submitInput="getDefination" />
      
      <span class="loader lg:mt-32 mt-10 ml-24 lg:ml-72" v-show="loading === true">Loading</span>
      <div class="grid grid-cols-1 gap-5">
        <DefinationCard v-for="( definition, index ) in  definitions" :key="index" :definition="definition" />
      </div>
    </div>
  </div>
</template>

