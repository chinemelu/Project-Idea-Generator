<template>
<div class="generator">
  <section class="hero is-primary is-bold has-text-centered py-6">
    <div class="hero-body">
      <div class="container">
        <h1 class="title">
          What skills do you want to work on?
        </h1>
        <div v-for="skill in skillList" :key="skill.id">
          <div class="field">
            <label class="checkbox">
              <input type="checkbox" :value="skill.id">
              {{ skill.skill }}
            </label>
          </div>
        </div>
      </div>
    </div>
  </section>
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