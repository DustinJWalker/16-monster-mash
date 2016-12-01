<template lang="html">
  <div class="app">


    <div class="sidebar">
      <div class="sidebar__heading"><p>Build Your Monster</p></div>
        <div class="img__switcher">
          <button @click="updatePart('body', -1)" class="btn"><i class="fa fa-chevron-left" aria-hidden="true"></i></button>
          <div class="sidebar__frame">
            <img class="sidebar__img" :src="'/monster/' + monsterParts.body[selected.body] + '.png'" alt="" />
          </div>
          <button @click="updatePart('body', 1)" class="btn"><i class="fa fa-chevron-right" aria-hidden="true"></i></button>

        </div>

        <div class="img__switcher">
          <button @click="updatePart('mouth', -1)" class="btn"><i class="fa fa-chevron-left" aria-hidden="true"></i></button>

          <div class="sidebar__frame">
              <img class="sidebar__img" :src="'/monster/' + monsterParts.mouth[selected.mouth] + '.png'" alt="" />
          </div>
          <button @click="updatePart('mouth', 1)"class="btn"><i class="fa fa-chevron-right" aria-hidden="true"></i></button>

        </div>

        <div class="img__switcher">
          <button @click="updatePart('eyes' -1)" class="btn"><i class="fa fa-chevron-left" aria-hidden="true"></i></button>

          <div class="sidebar__frame">
            <img class="sidebar__img" :src="'/monster/' + monsterParts.eyes.[selected.eyes] + '.png'" alt="" />
          </div>
          <button @click="updatePart('eyes' 1)" class="btn"><i class="fa fa-chevron-right" aria-hidden="true"></i></button>

        </div>

      <form class="sidebar__form" @submit.prevent="saveMonster">
        <input class="sidebar__input" type="text"  placeholder="Name Your Creation">
        <button class="sidebar__submit">Save Favorite!</button>
      </form>
    </div>



    <div class="app__hero">
      <div class="app__hero--content">
        <div class="big">
          <img class="big__img" :src="'/monster/' + monsterParts.body[selected.body] + '.full.png'"  alt="" />
          <img class="big__img" :src="'/monster/' + monsterParts.mouth[selected.mouth] + '.full.png'"  alt="" />
          <img class="big__img" :src="'/monster/' + monsterParts.eyes[selected.eyes] + '.full.png'"  alt="" />


        </div>
      </div>



<div class="favs">
  <div class="favs__grid">
  <div class="favs__row" v-for="favorite in favorites">
    <div class="favs__frame">
      <img class="favs__img" :src="'/monster/' + monsterParts.body[favorite.body] + '.full.png'" alt="" />
      <img class="favs__img" :src="'/monster/' + monsterParts.mouth[favorite.mouth] + '.full.png'" alt="" />
      <img class="favs__img" :src="'/monster/' + monsterParts.eyes[favorite.eyes] + '.full.png'" alt="" />


    </div>
    <div class="favs__name"><p>Name</p></div>
  </div>
</div>
</div>
</div>



</div>




      </template>

      <script>


import Vue from 'vue';
export default Vue.extend({
    data() {
        return {
          selected: {
            body: 0,
            mouth: 0,
            eyes: 0,
            name: '',
          },
          monsterParts,
          favorites: [],
        };
    },
  mounted() {
    this.getFavorites();
  },
  methods: {
    getFavorites(){
      fetch(`http://tiny-tn.herokuapp.com/collections/dw-monsters`)
      .then((r) => r.json())
      .then((favorites) => {
        this.favorites = favorites;
      });
    },
    updatePart(bodyPart, difference = 1) {
      this.selected[bodyPart] = (this.selected[bodyPart] + difference) % this.monsterParts[bodyPart].lenght;
    },
    saveMonster(){
      fetch(`http://tiny-tn.herokuapp.com/collections/dw-monsters`{
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(this.selected)
      })
      .then((r) => r.json())
      .then((favorite) => {
        this.favorites = [favorite, ...this.favorites];
        this.selected = {
          name: '',
          body: 0,
          eyes: 0,
          mouth: 0,
        };
      });
    },
  },
});
</script>

<style lang="css">
</style>
