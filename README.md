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
2. [How to use](#how-to-use)
3. [Try on](#try-on)
4. [Props](#props)
5. [Custom Example](#custom-example)
6. [Extra](#extra)

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

<h2 id="try-on">Try on:</h2>

[ReadMoreVal with Vue SFC Playground](https://sfc.vuejs.org/#eNqlWG1v2zYQ/itXYSiczZHbDtvQzElXtPswIC26pts+1N1AS7TNhCIVvjjpgvz3PaTerTZ1unxIJPLuubvnjndUbpLnZZluPU+OkrnjRSmZ4ycLRTTPxZa2h2J1vEikVut3/NotEsoksxZLiyRK1XKjVayXjfYDw1n+Shv+PHNiC/ycHj6kB8KetrCtFvRsyRRUN66QA9Mn81nY6gzMyr2N7WfLbrRxQ2Npmt5tb2Qu6H4phA5qPgN9n2Iy4P5TAPhQCnXR5/UzfA8z9mUa6JdMiuwCsqwWeVurDECJbm6oAaPb2565nuu75u9hPef72T/l1t5hf0Bk+9w8zWe92sarzYwoHZ75dYmcU85XzEtHN0FJsYIf0SJp/PmTyUUyDTs5c2xyUEkRvHLeqOaNqMlz0K0VKrEdLo5oxaTlrcCVULm++kvkbnNUv6RCKW7iUi12+3P4exvfSqNLe9QYbsy+hHPtIpH7WCKKM2eEWrem6jiPOhYXySl8K0iU1heUa6kNWeEIHLgpZVpZnrkQKLFclMJmgCMuhUvppVY8I8el9DYuTUkox00OIJaRZaXgijyWczwuIbTipuDKYb/0xtuUflOtMVoJFYUYMKbEPVjKhBRWWFL4ndKZtyVXubCWR3OkTSamPTFG1sPBElsSi0qwKSHpGTfM0ZZL4hZuvzFaKCq0xJvgZFEY3FSRw+wanmy19K6EToFTxsh4Z+DyVjjGh140LncuSLAVYshAXVHoXIcYHVANCZZ5CMHGNYVwQ2KElIxCBcLTQtRJaM2HsCHuBmlAyTGKETFifu3h0hvDuAWvJMXaA7CA1lIyOOlAP/HVSmQi6HLfbbCa1cY9i0NaMOcQRM3FQPXcW4dgXnjDlnEBBCIauvSsgDsacUE+nLKY57C1Nmwrcob1mOhSW8/RQzqydC70NBpu6wY5afVssBCs50IhSNQZYuT20nPaBCdQKPDCLAWhyJHLsAEaqgyANQW+4kPBkGvPALlCpcXsIAIUc0i3dQyF+GbDbFXIkdO6eJGUVhWEo5Qg0FTUFCdvidQBJvMGlUfwIhT1ax+yGssFdcrriq8Q690CzmWkoiC8QflDfcuMwB+bQQlQCAdnzIfy14pyAaXL8CbFEnyTEyoTuQcHA54GjQfyJvQb1G/TbqoO0nWlfTtG3Q8D4WjQnwAL/fm+YODWjsAKvXzFEe7vnhnz8Uz8O/bxtS/AwRj2h59+3AFz7KvBnj59MvZMSB5AMBL2xnn86NHYqfuCPBmB5Nxe3Bfl+x2U6jc6VenjXKph2nsQJpVXGFuov27sBQUVjil3Z40gHdPEwpkDOj7p5BpJ6wwE3EbYtL0L9QZ8alG+fPIIrSBADLYMj8dtMpvMJ+//Pvnw3cHJwWyN/hZG7FAUzSvbTGbpt8/eL/BD6YNnH2brgzg3B94Ep19otBKcnePgXHqOiTCJiJ0vh4/7qvWsH+g+G77imPUj3ImqxaoGefgRK5pEld4FgOYVyvgQ9Phv3emnoIIalGjPKBoR5tVdFscnZT+LXTGPzO2j3ivjnv6w1LuL42cK8v8zOUwdBs0aCCctQsfpro93G9+P1LuMd/SOLe+h3qO31u+f/EJjfvC8ozLqfINbsXuH2/kEG/3zXN9NWZ7/ukXFn2LoYtwanBzDQ5GjlVcIWr2NC01Gb5sHiWncv6/utoWwVosO1iE3EqlCWPIVJtIfKobSBVK7iput3vJ7eVszw91G591A2/1G6VdfBBl/8SA0jN0B66EVfxVS/GDYgWrcHgH06/B4/EExqoPQkfBh2nwSJdNEFOFOeliwMj23WuF/A9HCot7AzG6JWST450F4XyQb5/BZMpvZVRb+o3AOZs16hqfUIDei4Cm3xeHS6CvL0XOBEj2AA8ntf5U8arU=):

[ReadMorePre with Vue SFC Playground](https://sfc.vuejs.org/#eNqlWG1v2zYQ/itXYSiczpG7Ad3QzElXtBswIC2ypsM+1N1AS7TNVCJVvrjpgvz3PaSoN6tJ3cQfbIm8e+7uueOR9FXyvKrSrePJUTK3vKwKZvnJQhLNc7Gl7aFYHS+SQsn1W35pFwllBTMGQ4skSEW50SjGq0b7geYsf6U0f55ZsQV+Tg8f0gNhTlvYVgt6pmISqhtbFgPTJ/OZn+oMzKq9je1ny2yUtkNjaZrebm9kzut+LYQOaj4DfV9i0uP+WwL4sBDyQ5/XG/geZuzrNNCvWSGyD5BlUeRNVBmAEl1dUQNG19c9cz3Xd81/g/Wc72f/lBtzi/0Bke1z8zSf9WobrybTorJ45pcVck45XzFXWLrySpKV/IgWSefP1A/nzLLJQS1CcMk6LZs3oibJXjEq1GI7RBzRihWGtwKfhMzVp79FbjdH8SUVUnIdhqLY9S/+9zq8VVpV5qgx3Jh9CefaQSL7uUII51YLuW5NxSCPOgoXySl8K0lUxpWUq0JpMsISCLBTypQ0PLM+UGK5qITJAEe8EDall0ryjCwvCmfC0JSEtFznAGIZGVYJLslhOMfjEkIrrksuLeYrp51J6Q/ZGqOVkEGIAWNK3IGlTBTCCEMS3ymdO1NxmQtjeDBHSmdi2hNjZBwcrDBVYFAKNiVkPOOaWdrygriB22daCUmlKvAmOBlUBdd15DC7hidbVThbQafEEmOkndVweSss40MvGpc7Fwqw5WPIQF1Zqlz5GC1QNQmWOQjBxiX5cH1iRFEw8uUHT0sRk9Ca92FD3A7SgJJjFCJixNzawaUzzbgBr1SItQNgCa1lweCkBf3EVyuRCa/LXTfBIquNewYrtGTWIojIxUD1whmLYF44zZZhAAQiGvroWAl3FOKCvF9iIc9+aq3ZVuQM4yHRlTKOo4F0ZKlcqGkw3NYNctLqGW/BW8+FRJCoM8TIzUfHaeOdQKHAC70UhCJHLv0EaKgzANYk+AoPJUOuHQPkCpUWsoMIUMw+3cYyFOLZhpm6kAOnsXiRlFYVhKOUINBU1BQrb4nUASZzGpVH8MIX9WvnsxrKBXXKY8XXiHG2hHMZySAIb1D+UN8yLfBjMigBCuFgjTlf/kpSLqD00b8VYgm+yQqZidyBgwFPg8YDee37Deq3aTd1B+m60r4dIzZDT3jTDYdgvjl/Kxi4NSOwUi1fcYT7p2Nafz4X/419fO1KcDCGffLzTztglt0Z7OnTH8eeiYJ7kLMvEHcTzuP0ydip+4Pk3Hy4L0r9jU5VubAvRZj2EISdyklsW6i/btvzCtIvU27PG0E6pomBMwd0fNLJNZLGagjYjTBpexDq7e6pQfnyyWO0Ag8xmNI8LLfJbDKfvPvn5P33BycHszX6m99ih6JoXtlmMksfPXu3wIfSB8/ez9YHYd8ceOOdfqHQSrB2jr1z6QV2hElA7Hw5/KGvGvf6ge6z4SuWWT/CnaharHoj9x+xoklQ6R0AaF6jjBdBj//WnX4KaqiuRHsW0YWwWd1mbrxM9jMXK3lkax9dX8BWVTv6wyLvzos3lOL9ORwmDVvMGggnLUJkc9fB2y3vR+dtliOxY7N76PaIjfrjBnYDnRF9HNijXULQdg5Sq34XlzyfPG4SuNPh7mil64+3mOhFeUczvQ56o536u1TYZzHZggf973B1sG9xhZlgot/34hme5flvW3SGUxxOcCzR6DCa+2aALa9GUPJNGGhtNg8FTi39c/1u+/RjUXQwDrmRSB3Ckq+wc/8lQyhdINFV3ADUln+Tt5EZbjcq7zb+3YtcPx8BZHwtRGg4noyyeyekcLHagWrcHgH0S+J4fPEa1YHv3Li9N/fGZJqI0p/dD0tWpRdGSfyBEiws4gTONi0xiwT/sPj3RbKxFte32cysMv+3ywWY1esZnlKN3IiSp9yUh0utPhmOvQkowQM4kFz/D9lmyhg=):

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

<h2 id="custom-example">Custom Example:</h2>

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

<h2 id="extra">Extra</h2>

If you like `vue-read-more-esy`, please support it:

- [with a star on GitHub](https://github.com/kushaneranga/vue-read-more-esy)

Thank you!