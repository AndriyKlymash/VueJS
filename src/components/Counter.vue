<template>
  <div class="hello">
    counter is {{ counter }}
    <br>
    <button :class="counter > 0 ? 'isInced': 'isDeced'" @click="inc">INC</button>
    <button :class="{bold:true}" @click="$emit('handleDecClick')">DEC</button>
    <button :class="counter > 0 ? 'isInced' : 'isRes'" @click="$emit('handleResClick')">Reset</button>
  </div>
</template>

<script>
export default {
  props: {
    counter: {
      type: Number,
      required: true
    }
  },
  methods: {
    inc() {
      this.$emit('handleIncClick', 1, 2, 3);
    },
    //інший спосіб
    // dec(){
    //   this.$emit('handleDecClick');
    // }
  }
}
</script>

<style scoped>
.hello {
  background: #2c3e50;
  color: darkorange;
}

.bold {
  font-weight: bold;
}

.isInced {
  color: green;
}

.isDeced {
  color: red;
}

.isRes{
  color: grey;
}
</style>

