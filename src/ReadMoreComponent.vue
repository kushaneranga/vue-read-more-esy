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
      // windowWidth: window.innerWidth,
    };
  },
  props: {
    longTextData: {
      type: String,
      default: "",
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
      default: 480,
    },
    tabMediaQuarrySize: {
      type: Number,
      default: 992,
    },
    windowWidth: {
      type: [Number, String],
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
      return ((this.windowWidth - 40) / 3.2).toFixed(0) * 3;
    },
    tabSize: function () {
      return ((this.windowWidth - 40) / 14).toFixed(0) * 3;
    },
    desktopSize: function () {
      return ((this.windowWidth - 120) / 10).toFixed(0) * 3;
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
      // eslint-disable-next-line vue/no-mutating-props
      this.windowWidth = window.innerWidth;
    },
  },
};
</script>
