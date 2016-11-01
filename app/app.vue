<template lang="html">
  <div class="app">
    <div class="sidebar">
      <h3 class="sidebar__heading">Build Your Monster</h3>
        <div class="img__switcher">
          <button class="btn"></button>
          <i class="fa fa-chevron-left" aria-hidden="true"></i>
          <div class="sidebar__frame">
            <img class="sidebar__img" src="/monster/monsters-master/body-1.png" alt="" />
          </div>
          <button class="btn"></button>
          <i class="fa fa-chevron-right" aria-hidden="true"></i>
        </div>

        <div class="img__switcher">
          <button class="btn"></button>
          <i class="fa fa-chevron-left" aria-hidden="true"></i>
          <div class="sidebar__frame">
            <img class="sidebar__img" src="/monster/monsters-master/eyes-1-crossed.png" alt="" />
          </div>
          <button class="btn"></button>
          <i class="fa fa-chevron-right" aria-hidden="true"></i>
        </div>

        <div class="img__switcher">
          <button class="btn"></button>
          <i class="fa fa-chevron-left" aria-hidden="true"></i>
          <div class="sidebar__frame">
            <img class="sidebar__img" src="/monster/monsters-master/mouth-1.png" alt="" />
          </div>
          <button class="btn"></button>
          <i class="fa fa-chevron-right" aria-hidden="true"></i>
        </div>

      <form class="sidebar__form" action="index.html" method="post">
        <input class="sidebar__input" type="button" name="name" placeholder="Name Your Creation">
        <button class="sidebar__submit">Save Favorite!</button>
      </form>
    </div>
  </div>




      </template>

      <script>


import Vue from 'vue';
export default Vue.extend({
    data() {
        return {
            monsterParts: [],
            form: {
              name: 'monster-name'
            },
        };
    },
});
</script>

<style lang="css">
</style>
