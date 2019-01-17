<template>
  <div>

    <input type="text" class="form-control" v-model="search.wordFrom" v-on:keyup.enter="sendForm" placeholder="Please enter a word.">
    
    <select class="custom-select mr-sm-2 mt-3 mb-3" v-model="search.langPair">
      <option>Türkçe-İngilizce</option>
      <option selected>İngilizce-Türkçe</option>
    </select>
       
    <button type="submit" class="btn btn-primary mb-3" @click="sendForm">Search</button>

  </div>
</template>

<script>
export default {
  name: "SearchForm",
  data() {
    return {
      search: {
        wordFrom: "",
        wordTo: "",
        langPair: "İngilizce-Türkçe",
      }
    };
  },
  methods: {
      sendForm(){
          this.$emit('formSubmitted', this.search);
          this.$emit('showLoading');
      }
  }
};
</script>

<style scoped>
</style>
