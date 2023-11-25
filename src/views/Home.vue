<template>
  <div>home</div>
  <input v-model="search" type="text" name="" id="" />
  <p>search term: {{ search }}</p>
  <div v-for="name in matchingNames" :key="name">
    <p>{{ name }}</p>
  </div>
</template>

<script>
import { computed } from "@vue/reactivity";
import { ref, reactive, watch, watchEffect } from "vue";

export default {
  name: "Home",
  components: {},
  setup() {
    const names = ref(["mario", "yoshi", "shaun", "luigi"]);

    const search = ref("");

    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value));
    });

    /* watch(search, () => {
      console.log("watch function run");
    });
     */

    watchEffect(() => {
      console.log("watchEffect run", search.value);
    });

    return { names, search, matchingNames };
  },
  created() {},
  mounted() {},
};
</script>
