<script>
export default {
  props: {
    definition: {
        type : Object,
        required : true,
        /*
           {
			"definition": "The only country that [sounds good] as a [place's] name, as well as a [Pokemon's].",
			"permalink": "http://myanmar.urbanup.com/4823728",
			"thumbs_up": 219,
			"author": "Kaimatten",
			"word": "Myanmar",
			"defid": 4823728,
			"current_vote": "",
			"written_on": "2010-03-23T07:14:55.000Z",
			"example": "\"Go Myanmar! Use [Quick Attack] on Bangladesh! Flame Thrower to Human Rights! [Defense Curl] on that Opium!\"\n\n\"Myanmar! [Myan]! Myan! Mar!\"",
			"thumbs_down": 64
		  },
        */
    },
  },
  data() {
    return {};
  },
};
</script>

<template>
  <div
    class="bg-white shadow-xl p-5 rounded-lg border border-slate-100 w-full min-h-36 mt-10"
  >
    <!-- Header -->
    <h1 class="text-orange-500 text-2xl font-semibold">{{ definition.word }}</h1>
    <!-- Content -->
    <p class="mt-3 font-semibold">
       {{ definition.definition }}
    </p>
    <!-- footer -->
    <p class="mt-3 font-semibold text-lg text-black">
        By 
        <span class="text-orange-500">{{ definition.author }}</span> 
        <span class="text-black ml-3">{{ new Date(definition.written_on).toLocaleDateString() }}</span>
    </p>
  </div>
</template>
