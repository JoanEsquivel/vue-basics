<template>
  <h1> {{title.toUpperCase()}}</h1>
  <h2 v-html="subtitle"></h2>
  <p v-if="isShowing">V-If example</p>
  <p v-else>V-Else example</p>
  <p v-show="isShowing">I am a V-SHOW example</p>
  <p v-text="text"></p>
  <ul>
    <li v-for="(value, key) in heros" v-bind:key="value">{{key}} {{value}}</li>
  </ul>
  <h3>Printing an array of objects</h3>
  <ul>
    <li v-for="(hero, index) in herosArrayOfObjects" v-bind:key="index">{{index+1}} {{hero.name}}</li>
  </ul>
  <button :disabled="isDisabled">V-Binding attribute values</button>

  <p>V Model Example - Two Way Data Biding:</p>
  <input type="text" v-model="newHero">
  <button> V-Model: {{newHero}} </button>

  <!-- 01:34:25 -->
</template>

<script>
  export default {
    data (){
      return{
        title: "DC Heros",
        subtitle: "<h2>I am a subtitle with v-html directive[Not recommended]</h2>",
        isShowing: false,
        text: "I am a text. Using v-text",
        heros:{
          Batman: "Batman",
          Flash: "Flash",
          Superman: "Superman"
        },
        herosArrayOfObjects: [
          {name: "Batman"},
          {name: "Superman"},
          {name: "flash"}
        ],
        isDisabled: true,
        newHero: 'Aquaman'
      }
    }
  }

</script>