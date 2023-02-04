<template>
  <div v-if="longText" class="about-the-gallery">
    <div class="primary-color-text s-gallery-text">
      <p v-if="!readMoreActivated && !isLongText">
        <span v-html="longText"></span>
      </p>
      <p v-if="!readMoreActivated && isLongText">
        <span v-html="shortText"></span>...
      </p>
      <p v-if="readMoreActivated"><span v-html="longText"></span></p>
    </div>
    <div class="read_more-link">
      <div class="primary-color-text s-gallery-text">
        <div v-if="!readMoreActivated && isLongText" @click="activateReadMore">
          {{ readmore }}
        </div>
        <div v-if="readMoreActivated && isLongText" @click="deactivateReadMore">
          {{ readless }}
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
    longtextdata: {
      type: String,
      default:
        "dadadasdadasdadas dassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdassdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadasdadadasdadasdadasdas sdasdasdasdasdasdaseddasdasdasdasdasdasdasdasdasddsadadas",
    },
    readmore: {
      type: String,
      default: "Read more",
    },
    readless: {
      type: String,
      default: "Read less",
    },
  },
  computed: {
    shortText: function () {
      if (this.windowWidth < 480) {
        let str = this.longText
          .slice(0, this.mobileSize)
          .replace(/(<([^>]+)>)/gi, "")
          .match(/.*?[\\ !?]/g);
        console.warn(str);
        let nstr = str.join("").slice(0, -1);
        return nstr ? nstr : this.longText.slice(0, this.mobileSize);
      }
      if (this.windowWidth < 992) {
        let str = this.longText
          .slice(0, this.tabSize)
          .replace(/(<([^>]+)>)/gi, "")
          .match(/.*?[\\ !?]/g);
        console.warn(str);
        let nstr = str.join("").slice(0, -1);
        return nstr ? nstr : this.longText.slice(0, this.tabSize);
      }
      let str = this.longText
        .slice(0, this.desktopSize)
        .replace(/(<([^>]+)>)/gi, "")
        .match(/.*?[\\ !?]/g);
      console.warn(str);
      let nstr = str.join("").slice(0, -1);
      return nstr ? nstr : this.longText.slice(0, this.desktopSize);
    },
    isLongText: function () {
      if (this.windowWidth < 480) {
        return this.longText.length > this.mobileSize;
      }
      if (this.windowWidth < 992) {
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
    console.log(this.readmore);
    let longtextdata = this.longtextdata;
    console.log(longtextdata);
    this.longText = longtextdata;
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
