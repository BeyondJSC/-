<template>
  <div id="app">
    <h1 class="text-primary">在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm @formSubmit="translateText"></translateForm>
    <translateOutput :translatedText="translatedText"></translateOutput>
  </div>
</template>

<script>
import translateForm from './components/form'
import translateOutput from './components/output'

export default {
  name: 'App',
  components: {
    translateForm,
    translateOutput
  },
  data () {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText: function(text, language) {
      // console.log(text)
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180923T073619Z.fe8644f5d3e696d6.334cd20ba42eb82df6045aee6627c0c9e5f2de92&lang='+ language +'&text='+text).then((res)=>{
        // console.log(res.body.text[0]);
        this.translatedText = res.body.text[0];
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
