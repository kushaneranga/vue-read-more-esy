<p align="center">
  <a href="https://github.com/kushaneranga/vue-read-more-esy" target="_blank" rel="vue read more"><img src="https://user-images.githubusercontent.com/61194721/217131808-fa12c011-142f-4c0c-88a7-fbc262ec1cbf.png" alt="my banner"></a>
</p>
<div align="center">
  <h1>vue-read-more-esy</h1>
  <p>
    "vue-read-more-esy" is a Vue.js package that offers a convenient way to display text content with a responsive design and customizable word count. It features a "read more" button that allows the user to expand and read the full text. This package is easy to use and provides a great way to manage long text content in a user-friendly manner.
  </p>
</div>

## Table of Contents
1. [Setup](#setup)
3. [How to use](#how-to-use)
4. [Props](#props)
5. [Custom Example](#custom-example)

<h2 id="setup">Setup</h2>

Install with npm:

```bash
npm i vue-read-more-esy
```

<h2 id="how-to-use">How to use</h2>

This allows you to break text with common punctuations like space, dot ('.'), exclamation mark ('!'), and question mark ('?'). Breaking text with these characters creates a visually appealing and easy-to-read layout for displaying lengthy text content.

Add dependencies to your `main.js`:

You want to handle text character count based on screen size percentage:

```javascript
import Vue           from 'vue'
import ReadMorePre from 'vue-read-more-pre'

Vue.use(ReadMorePre)
```

Add the global component to your `App.vue`:

```vue
<ReadMorePre longTextData="Lorem.ipsum dolor sit amet, consectetur adipiscing elit. Donec tellus elit,....."><ReadMorePre/>
```

You want to handle number of characters:

```javascript
import Vue           from 'vue'
import ReadMoreVal from 'vue-read-more-val'

Vue.use(ReadMoreVal)
```

Add the global component to your `App.vue`:

```vue
<ReadMoreVal longTextData="Lorem.ipsum dolor sit amet, consectetur adipiscing elit. Donec tellus elit,....."><ReadMorePre/>
```

<p><b>Use the component directly:</b></p>

```html
<!-- read-more.vue -->
<template>
  <ReadMorePre longTextData="Lorem.ipsum dolor sit amet, consectetur adipiscing elit. Donec tellus elit,....."><ReadMorePre/>

  <!-- Or -->

  <ReadMoreVal longTextData="Lorem.ipsum dolor sit amet, consectetur adipiscing elit. Donec tellus elit,....."><ReadMoreVal/>
</template>

<script>
  import { ReadMorePre } from 'vue-read-more-pre';
  // Or
  import { ReadMoreVal } from 'vue-read-more-val';

  export default {
    components: {
      ReadMorePre,
      // Or
      ReadMoreVal.
    },
  };
</script>
```

<h2 id="props">Props</h2>

Note that all props are optional.

Common props:

| Name              | Type          | Default            | Description                                                  |
| ----------------  | ------------- | ------------------ | ------------------------------------------------------------ |
| longTextData      | String        | ''                 | Used to pass large amounts of text data (Required data)      |
| readMore          | String        | Read more          | But you can use any text that you prefer.                    |
| readLess          | String        | Read less          | But you can use any text that you prefer.                    |
| mobMediaQuarrySize| Number        | 576                | Package uses a media breakpoint query of 576px for mobile screen sizes. However, this value is customizable, and you can adjust it to meet your specific needs.                          |
| tabMediaQuarrySize| Number        | 992                | Package uses a media breakpoint query of 992px for Tab screen sizes. However, this value is customizable, and you can adjust it to meet your specific needs.                          |

ReadMorePre props:

| Name              | Type          | Default            | Description                                                  |
| ----------------  | ------------- | ------------------ | ------------------------------------------------------------ |
| mobileSizePre     | Number        | 0.5                | Allows you to specify the percentage of text that should appear on the <b>mobile</b> screen based on the screen size. By default, the value is set to 0.5, meaning that 50% of the text content will appear on the <b>mobile</b> screen. <b>this value is customizable</b>                                      |
| tabSizePre        | Number        | 0.5                | Allows you to specify the percentage of text that should appear on the <b>Tab</b> screen based on the screen size. By default, the value is set to 0.5, meaning that 50% of the text content will appear on the <b>Tab</b> screen. <b>this value is customizable</b>                                                 |
| deskSizePre       | Number        | 0.5                | Allows you to specify the percentage of text that should appear on the <b>Desktop</b> screen based on the screen size. By default, the value is set to 0.5, meaning that 50% of the text content will appear on the <b>Desktop</b> screen. <b>this value is customizable</b>                                     |

ReadMoreVal props:

| Name              | Type          | Default            | Description                                                  |
| ----------------  | ------------- | ------------------ | ------------------------------------------------------------ |
| mobileSizeVal     | Number        | 100                | Maximum number of characters that should appear on the <b>mobile</b> screen.                                                                                                              |
| tabSizeVal        | Number        | 200                | Maximum number of characters that should appear on the <b>Tab</b> screen.                                                                                                                 |
| deskSizeVal       | Number        | 300                | Maximum number of characters that should appear on the <b>Desktop</b> screen.                                                                                                  |

<h1 id="custom-example">Custom Example:</h1>

```vue
<ReadMoreVal
  longTextData="
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec tellus elit, interdum ac sapien ut, dapibus fermentum purus. In sit amet finibus ante, eu facilisis nisi. Suspendisse elit orci, facilisis a suscipit lacinia, placerat vel est. Proin molestie semper dolor, eget volutpat massa rutrum vitae. Suspendisse finibus facilisis lectus ac commodo.
  "
  readMore="See more"
  readLess="See less"
  :mobMediaQuarrySize="575"
  :tabMediaQuarrySize="767"
  :mobileSizeVal="80"
  :tabSizeVal="180"
  :deskSizeVal="280"
>
</ReadMoreVal>

<!-- Or -->

<ReadMorePre
  longTextData="
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec tellus elit, interdum ac sapien ut, dapibus fermentum purus. In sit amet finibus ante, eu facilisis nisi. Suspendisse elit orci, facilisis a suscipit lacinia, placerat vel est. Proin molestie semper dolor, eget volutpat massa rutrum vitae. Suspendisse finibus facilisis lectus ac commodo.
  "
  readMore="See more"
  readLess="See less"
  :mobMediaQuarrySize="575"
  :tabMediaQuarrySize="767"
  :mobileSizePre="0.3"
  :tabSizePre="0.5"
  :deskSizePre="0.4"
>
</ReadMorePre>
```