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
  name: "ReadMore",
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
      default: "",
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
    mobileSizePre: {
      type: Number,
      default: 0.5,
    },
    tabSizePre: {
      type: Number,
      default: 0.5,
    },
    deskSizePre: {
      type: Number,
      default: 0.5,
    },
  },
  computed: {
    shortText: function () {
      if (this.windowWidth < this.mobMediaQuarrySize) {
        let str = this.longText
          .slice(0, this.mobileSize)
          .replace(/(<([^>]+)>)/gi, "")
          .match(/.*?[\\ !?]/g);
        let shortContent = str.join("").slice(0, -1);
        return shortContent
          ? shortContent
          : this.longText.slice(0, this.mobileSize);
      }
      if (this.windowWidth < this.tabMediaQuarrySize) {
        let str = this.longText
          .slice(0, this.tabSize)
          .replace(/(<([^>]+)>)/gi, "")
          .match(/.*?[\\ !?]/g);
        let shortContent = str.join("").slice(0, -1);
        return shortContent
          ? shortContent
          : this.longText.slice(0, this.tabSize);
      }
      let str = this.longText
        .slice(0, this.desktopSize)
        .replace(/(<([^>]+)>)/gi, "")
        .match(/.*?[\\ !?]/g);
      let shortContent = str.join("").slice(0, -1);
      return shortContent
        ? shortContent
        : this.longText.slice(0, this.desktopSize);
    },
    isLongText: function () {
      if (this.windowWidth < this.mobMediaQuarrySize) {
        return this.longText.length > this.mobileSize;
      }
      if (this.windowWidth < this.tabMediaQuarrySize) {
        return this.longText.length > this.tabSize;
      }
      return this.longText.length > this.desktopSize;
    },
    mobileSize: function () {
      return (this.windowWidth * this.mobileSizePre).toFixed(0);
    },
    tabSize: function () {
      return (this.windowWidth * this.tabSizePre).toFixed(0);
    },
    desktopSize: function () {
      return (this.windowWidth * this.deskSizePre).toFixed(0);
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
