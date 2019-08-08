<template>
  <div class="row" id="translateForm">
    <div class="col-md-6 col-md">
    <form v-on:submit="formSubmit">
      <input type="text" v-model="textToTranslate" placeholder="输入要翻译的内容">
      <select v-model="language">
        <option value="en">English</option>
        <option value="ru">Russian</option>
        <option value="ko">Korean</option>
        <option value="ja">Janpenese</option>
      </select>
      <input type="submit" value="翻译">
    </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data: function () {
    return {
      textToTranslate: '',
      language: ''
    }
  },
  methods: {
    formSubmit: function (e) {
      // alert(this.textToTranslate);
      this.$emit('formSubmit', this.textToTranslate, this.language)
      e.preventDefault()
    }
  }
}
</script>

<style>

</style>
