<template>
  <div class="root">
    <div class="troll">
      <h2>{{title}}</h2>
      <form v-on:submit="addStarship" method="post">
          <div class="tnl-FormsGroup">
            <label for="">Ponle un nombre:</label>
            <input type="text" name="" value="" v-model="newStarship.name">
          </div>
          <div class="tnl-FormsGroup">
            <label for="">Añade el modelo:</label>
            <input type="text" name="" value="" v-model="newStarship.model">
          </div>
          <div class="tnl-FormsGroup">
            <label for="">Añade el la imagen:</label>
            <input type="text" name="" value="" v-model="newStarship.picture">
          </div>
          <button type="submit" name="button" class="tnl-Button-cta">Añadir nave</button>
      </form>
    </div>
    <ul class="tnl-ListCell">
        <li class="tnl-ListCell_Item-picture">
          <a class="tnl-ListCell_Arrow-right" href="#"></a>
            <div class="tnl-ListCell_Picture">
              <img :src="newStarship.picture" alt="">
            </div>
            <div class="tnl-ListCell_MainData">
                <p class="tnl-ListCell_Title">{{newStarship.name}}</p>
                <p class="tnl-ListCell_Description">{{newStarship.model}}</p>
            </div>
        </li>
        <li v-for="starship in starships"
            v-bind:class="[starship.hasImage ? 'tnl-ListCell_Item-picture' : 'tnl-ListCell_Item']">
          <a class="tnl-ListCell_Arrow-right" href="#"></a>
            <div class="tnl-ListCell_Picture" v-show="starship.hasImage">
              <img :src="starship.picture" alt="">
            </div>
            <div class="tnl-ListCell_MainData">
                <p class="tnl-ListCell_Title">{{starship.name}}</p>
                <p class="tnl-ListCell_Description">{{starship.model}}</p>
            </div>
        </li>
    </ul>
  </div>
</template>


<script>
import axios from 'axios'

export default {
  name: 'list',
  data() {
      return {
        title: 'Añade una nave',
        newStarship: {
          name: '',
          model: '',
          picture: '',
          hasImage: false,
        },
        starships: [],
      }
  },
  // created: function() {
  //   axios.get('https://swapi.co/api/starships/')
  //     .then( response => {
  //       this.starships = response.data.results.reverse();
  //     });
  // },
  methods: {
    addStarship: function(e) {
      e.preventDefault();
      this.starships.push({
        name: this.newStarship.name,
        model: this.newStarship.model,
        picture: this.newStarship.picture,
        hasImage: this.newStarship.picture != '',
      });
    }
  }

}
</script>

<style scoped>
  .troll {
    padding: 1em;
  }
</style>
