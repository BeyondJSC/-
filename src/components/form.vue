<template>
  <div class="row" id="translateForm">
    <div class="col-md-6 col-md-offset-3">
        <form @submit="formSubmit" class="well form-inline _transform">
            <input class="form-control" type="text" placeholder="输入需要翻译的内容" v-model="textToTranslate">
            <select v-model="language" class="form-control">
                <option value="en">English</option>
                <option value="ru">Russian</option>
                <option value="ko">Korean</option>
                <option value="ja">Janpenese</option>
                <option value="fr">French</option>
            </select>
            <input class="btn btn-primary" type="submit" value="翻译">
        </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data () {
      return {
          textToTranslate: '',
          language: ''
      }
  },
  methods: {
      formSubmit: function(e) {
          this.$emit("formSubmit", this.textToTranslate, this.language)
          e.preventDefault();
      }
  },
  created: function() {
      this.language = 'en';
  }
}
</script>

<style>
    ._transform{
        border-radius: 10px;
        border: 1px solid #ccc;
        justify-content: center;
    }
</style>