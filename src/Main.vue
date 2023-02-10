<template>
  <div class="align-center margin">
    <input
      type="range"
      :min="min"
      :max="max"
      v-model="currentValue"
      class="myRange"
      :style="{ width: max + 'px' }"
    />
    <p>{{ currentValue }}px</p>
    <div id="widthBox" :style="{ width: currentValue + 'px' }">
      <ReadMore :windowWidth="currentValue" :longTextData="text"></ReadMore>
    </div>
  </div>
</template>

<script>
import ReadMore from "./ReadMoreComponent.vue";
export default {
  name: "DemoPage",
  data() {
    return {
      min: 80,
      max: null,
      currentValue: 120,
      widthReduce: null,
      text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec tellus elit, interdum ac sapien ut, dapibus fermentum purus. In sit amet finibus ante, eu facilisis nisi. Suspendisse elit orci, facilisis a suscipit lacinia, placerat vel est. Proin molestie semper dolor, eget volutpat massa rutrum vitae. Suspendisse finibus facilisis lectus ac commodo. Integer iaculis, ex et fringilla porta, mi ipsum volutpat nisi, et consectetur urna erat a augue. Praesent ligula mi, blandit ut efficitur eu, blandit a nisi. Integer sed mattis dolor, ut efficitur justo. Curabitur mollis quam eros, ut tempus felis gravida ut. In posuere facilisis odio, sed interdum est gravida sollicitudin. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Phasellus augue sapien, malesuada at lacus placerat, lobortis cursus risus. Nulla vitae elementum sapien. Nullam nec nulla ac metus varius scelerisque. Duis non diam quis libero tincidunt sollicitudin.",
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
#widthBox {
  display: block;
  height: auto;
  margin: auto;
}
.align-center {
  text-align: center;
}
.margin {
  margin-top: 50px;
}
</style>
