<template>
  <img v-bind:alt="imageAlt" :src="imageSrc">
  <div class="mainBox">
    {{ title }}
    <p>{{ paragraph }}</p>
    <ul>
      <li v-for="(item, index) of items" :key="item">{{ item }}
        <button @click="itemRemove(item, index)">remove</button>
      </li>
    </ul>

    <h2 v-if="counter === 0">Hello</h2>
    <h2 v-else-if="counter === 1">1</h2>
    <h2 v-else-if="counter === 2">2</h2>
    <h2 v-else-if="counter === 3">3</h2>
    <h2 v-else>World</h2>

    <div class="counterBox">
      <div>
        <Counter :counter="counter" @handleIncClick="incHandler" @handleDecClick="decHandler"/>
      </div>
      <div>
        <Counter :counter="counter" @handleIncClick="incHandler" @handleDecClick="decHandler"
                 @handleResClick="resetHandler"/>
      </div>
    </div>
  </div>


</template>

<script>
import Img from './assets/logo.png'
import Counter from "./components/Counter";

export default {
  name: 'App',
  components: {
    Counter
  },
  data() {
    return {
      counter: 0,
      title: 'Dynamic text',
      paragraph: 'This is paragraph',
      imageAlt: 'Vue logo',
      imageSrc: Img,
      items: [1, 2, 3, 4]
    }
  },
  methods: {
    incHandler(a, b, c) {
      console.log(a, b, c);
      // console.log(this);
      this.counter++;
    },

    decHandler() {
      if (this.counter > 0) {
        this.counter--;
      }
    },

    resetHandler() {
      this.counter = 0;
    },

    itemRemove(item, index) {
      this.items.splice(index, 1);
    }
  }
}
</script>
<style>
.counterBox {
  display: flex;
  column-gap: 20px;
}

</style>
