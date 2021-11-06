<template>
  <ul>
    <li
      class="flex justify-between"
      v-for="(hero, index) in herosArrayOfObjects"
      :key="hero.name"
    >
      <div>
        {{ hero.name }}
      </div>
      <button @click="removeHero(index)">x</button>
    </li>
  </ul>

  <form class="mt-10" @submit.prevent="addHero()">
    <input
      class="border rounded"
      type="text"
      v-model="newHero"
      placeholder="Type a new hero here"
    />
    <button
      class="
        border
        rounded
        bg-gradient-to-t
        from-red-200
        to-green-200
        text-sm
        ml-10
      "
      @click="newHero"
    >
      Add a new hero
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      herosArrayOfObjects: [
        { name: "Batman" },
        { name: "Superman" },
        { name: "flash" },
      ],
    };
  },
  methods:{
      addHero() {
      if (this.newHero !== "") {
        this.herosArrayOfObjects.push({ name: this.newHero });
        this.newHero = "";
      }
    },
    removeHero(index) {
      this.herosArrayOfObjects = this.herosArrayOfObjects.filter(
        (hero, i) => i != index
      );
    },
  }
};
</script>

<style>
</style>