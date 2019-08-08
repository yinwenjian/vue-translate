<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-mited">简单 / 易用 / 便捷</h5>
    <translateForm v-on:formSubmit="translateText"></translateForm>
    <translate-output v-text="translatedText"> </translate-output>
  </div>
</template>

<script>

// eslint-disable-next-line no-unused-vars
import TranslateForm from './components/TranslateForm'
// eslint-disable-next-line no-unused-vars
import TranslateOutput from './components/TranslateOutput'
export default {
  name: 'app',
  data: function () {
    return {
      translatedText: ''
    }
  },
  components: {
    TranslateForm, TranslateOutput
  },
  methods: {
    translateText: function (text,language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190808T083026Z.2e230fe41980f3ab.ad6cc256986edfed09e6a34e7e0fd193af6cd970&lang=' + language + '&text=' + text)
        .then((response) => {
          // console.log(response.body.text[0])
          this.translatedText = response.body.text[0]
        })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
