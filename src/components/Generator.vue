<template>
  <div>

  </div>
</template>

<script>
  import { ref } from 'vue';
  export default {
    name: 'Generator',
    setup() {
      const GENERATOR_BASE = 'http://localhost:3000';
      const skillList = ref([]);

      async function getSkillList() {
        const response = await fetch(`${GENERATOR_BASE}/skills`);
        skillList.value = await response.json();
      }

      getSkillList();

      return {
        skillList,
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>