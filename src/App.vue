<template>
  <h1>{{ title.toUpperCase() }}</h1>
  <h2 v-html="subtitle"></h2>
  <p v-if="isShowing">V-If example</p>
  <p v-else>V-Else example</p>
  <p v-show="isShowing">I am a V-SHOW example</p>
  <p v-text="text"></p>
  <ul>
    <li v-for="(value, key) in heros" v-bind:key="value">
      {{ key }} {{ value }}
    </li>
  </ul>
  <h3>Printing an array of objects</h3>
  <ul>
    <li v-for="(hero, index) in herosArrayOfObjects" v-bind:key="index">
      {{ index + 1 }} {{ hero.name }}
    </li>
  </ul>

  <!-- v-bind -> : -->
  <button :disabled="isDisabled">V-Binding attribute values</button>

  <p>V Model Example - Two Way Data Biding:</p>
  <input type="text" v-model.trim="newHero" />
  <button>V-Model: {{ newHero }}</button>

  <p>V-ON Example</p>

  <!-- V-on -> @ -->
  <button @click="von = 'Text after click with V-on'">
    Click to trigguer V-ON
  </button>
  <button @keydown="von = 'Text after keydown'">Key down example</button>
  <input type="text" v-model="von" />

  <p>Form example</p>
  <form @submit.prevent="formText = 'New text from FORM Submit'">
    <input type="text" v-model="formText" />
    <button type="submit">Send text by form</button>
  </form>

  <p>Adding heros to the list - Heros count {{ herosCount }}</p>
  <h2>{{ fullname }}</h2>
  <button @click="setFullName">Set Full name</button>
  <h2>{{fname}}</h2>
  <h2>{{lname}}</h2>
  <p>Computed: {{ randC }}</p>
  <p>Computed: {{ randC }}</p>
  <p>Computed: {{ randC }}</p>
  <p>Method: {{ randM() }}</p>
  <p>Method: {{ randM() }}</p>
  <p>Method: {{ randM() }}</p>
  <ul>
    <li v-for="(hero, index) in herosArrayOfObjects" v-bind:key="index">
      {{ hero.name }}
    </li>
  </ul>

  <form @submit.prevent="addHero()">
    <input type="text" v-model="newHero" placeholder="Type a new hero here" />
    <button @click="newHero">Add a new hero</button>
  </form>

  <p>Total Heros is {{ herosCount }}</p>

  <h1>Adding heros to the list properly</h1>

  <ul>
    <li v-for="(hero, index) in herosArrayOfObjects" v-bind:key="index">
      <div>{{ hero.name }} <button @click="removeHero(index)">x</button></div>
    </li>
  </ul>

  <form @submit.prevent="addHero()">
    <input type="text" v-model="newHero" placeholder="Type a new hero here" />
    <button @click="newHero">Add a new hero</button>
  </form>

  <!-- 2:17:02 -->
</template>

<script>
export default {
  data() {
    return {
      title: "DC Heros",
      subtitle:
        "<h2>I am a subtitle with v-html directive[Not recommended]</h2>",
      isShowing: false,
      text: "I am a text. Using v-text",
      heros: {
        Batman: "Batman",
        Flash: "Flash",
        Superman: "Superman",
      },
      herosArrayOfObjects: [
        { name: "Batman" },
        { name: "Superman" },
        { name: "flash" },
      ],
      isDisabled: true,
      newHero: "Aquaman",
      von: "V-On Example",
      formText: "Form Text",
      fname: "Joan",
      lname: "Eesquivel",
    };
  },
  methods: {
    //Can not be an arrow function cause does not hold this keyword.
    addHero() {
      if (this.newHero !== "") {
        this.herosArrayOfObjects.push({ name: this.newHero });
        this.newHero = "";
      }
    },
    removeHero(index){
      this.herosArrayOfObjects = this.herosArrayOfObjects.filter((hero, i) => i != index)
    },
    randM() {
      return Math.random();
    },
    setFullName(){
      
      this.fullname = 'New Name'

    }
  },
  computed: {
    herosCount() {
      return this.herosArrayOfObjects.length;
    },
    randC() {
      return this.herosArrayOfObjects.length + Math.random();
    },
    fullname: {
      get() {
        return this.fname + " " + this.lname;
      },
      set(fullname){
        const values = fullname.split(" ")
        this.fname = values[0]
        this.lname = values[1]
      }
    },
  },
};
</script>