<template>
  <div v-if="longText" class="">
    <div class="">
      <p v-if="!readMoreActivated && !isLongText">
        <span v-html="longText"></span>
      </p>
      <p v-if="!readMoreActivated && isLongText">
        <span v-html="shortText"></span>...
      </p>
      <p v-if="readMoreActivated"><span v-html="longText"></span></p>
    </div>
    <div class="read_more-link">
      <div class="">
        <div v-if="!readMoreActivated && isLongText" @click="activateReadMore">
          {{ readMore }}
        </div>
        <div v-if="readMoreActivated && isLongText" @click="deactivateReadMore">
          {{ readLess }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ReadMoreVal",
  data() {
    return {
      longText: "",
      readMoreActivated: false,
      windowWidth: window.innerWidth,
    };
  },
  props: {
    longTextData: {
      type: String,
      default:
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec tellus elit, interdum ac sapien ut, dapibus fermentum purus. In sit amet finibus ante, eu facilisis nisi. Suspendisse elit orci, facilisis a suscipit lacinia, placerat vel est. Proin molestie semper dolor, eget volutpat massa rutrum vitae. Suspendisse finibus facilisis lectus ac commodo. Integer iaculis, ex et fringilla porta, mi ipsum volutpat nisi, et consectetur urna erat a augue. Praesent ligula mi, blandit ut efficitur eu, blandit a nisi. Integer sed mattis dolor, ut efficitur justo. Curabitur mollis quam eros, ut tempus felis gravida ut. In posuere facilisis odio, sed interdum est gravida sollicitudin. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Phasellus augue sapien, malesuada at lacus placerat, lobortis cursus risus. Nulla vitae elementum sapien. Nullam nec nulla ac metus varius scelerisque. Duis non diam quis libero tincidunt sollicitudin.",
      required: true,
    },
    readMore: {
      type: String,
      default: "Read more",
    },
    readLess: {
      type: String,
      default: "Read less",
    },
    mobMediaQuarrySize: {
      type: Number,
      default: 576,
    },
    tabMediaQuarrySize: {
      type: Number,
      default: 992,
    },
    mobileSizeVal: {
      type: Number,
      default: 100,
    },
    tabSizeVal: {
      type: Number,
      default: 200,
    },
    deskSizeVal: {
      type: Number,
      default: 300,
    },
  },
  computed: {
    shortText: function () {
      const sizes = [this.mobileSizeVal, this.tabSizeVal, this.deskSizeVal];
      const getShortText = (size) => {
        const str = this.longText
          .slice(0, size)
          .replace(/(<([^>]+)>)/gi, "")
          .match(/.*?[\\ !?]/g);
        const shortContent = str.join("").slice(0, -1);
        return shortContent ? shortContent : this.longText.slice(0, size);
      }
      if (this.windowWidth < this.mobMediaQuarrySize) {
        return getShortText(sizes[0]);
      } else if (this.windowWidth < this.tabMediaQuarrySize) {
        return getShortText(sizes[1]);
      } else {
        return getShortText(sizes[2]);
      }
    },
    isLongText: function () {
      if (this.windowWidth < this.mobMediaQuarrySize) {
        return this.longText.length > this.mobileSizeVal;
      }
      if (this.windowWidth < this.tabMediaQuarrySize) {
        return this.longText.length > this.tabSizeVal;
      }
      return this.longText.length > this.deskSizeVal;
    },
  },
  mounted() {
    this.$nextTick(() => {
      window.addEventListener("resize", this.onResize);
    });
    let longTextData = this.longTextData;
    this.longText = longTextData;
  },
  beforeUnmount() {
    window.removeEventListener("resize", this.onResize);
  },
  methods: {
    activateReadMore() {
      this.readMoreActivated = true;
    },
    deactivateReadMore() {
      this.readMoreActivated = false;
    },
    onResize() {
      this.windowWidth = window.innerWidth;
    },
  },
};
</script>
