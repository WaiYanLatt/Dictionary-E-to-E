<script>
export default {
  emits : ['submitInput'],
  data() {
    return {
      searchQuery: "",
    };
  },
};
</script>

<template>
  <form action="#" class="shadow-lg" @submit.prevent="$emit('submitInput' , searchQuery)">
    <input
      class="w-full py-3 border-2 border-slate-500 px-5 rounded-lg focus:outline-none font-semibold focus:border-orange-500"
      type="text"
      placeholder="Search Something"
      v-model="searchQuery"
    />
  </form>
</template>
