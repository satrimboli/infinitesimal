<template>
  <transition :name="transition">
    <div v-show="isShowing" :class="cssClasses">
      <slot></slot>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'TypeUnit',
  props: {
    currentTime: Number,
    start: Number,
    end: {
      type: Number,
      default: 100
    },
    transition: String,
    cssClasses: String
  },
  data: function() {
    return {}
  },
  computed: {
    isShowing: function() {
      if(this.currentTime > this.start && this.currentTime < this.end) {
        return true;
      } else {
        return false;
      }
    }
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
