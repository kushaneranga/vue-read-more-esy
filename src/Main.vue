<template>
  <div>
    <input
      type="range"
      :min="min"
      :max="max"
      v-model="currentValue"
      class="myRange"
      :style="{ width: max + 'px' }"
    />
    <p>{{ currentValue }}</p>
    <div class="widthBox" :style="{ width: currentValue + 'px' }">
      <ReadMore></ReadMore>
    </div>
  </div>
</template>

<script>
import ReadMore from "./ReadMoreComponent.vue";
export default {
  name: "Main",
  data() {
    return {
      min: 0,
      max: null,
      currentValue: 50,
      widthReduce: null,
    };
  },
  components: {
    ReadMore,
  },
  created() {
    window.resizeTo(800, 600);
  },
  mounted() {
    this.widthReduce = window.innerWidth * 0.2;
    this.max = window.innerWidth - this.widthReduce;
    console.log(this.max);
  },
  methods: {
    windowWidth() {
      this.max = window.innerWidth - 200;
    },
  },
};
</script>

<style>
.myRange {
  width: 100%;
}
.widthBox {
  display: block;
  background: rgb(20, 208, 214);
  height: auto;
}
</style>
