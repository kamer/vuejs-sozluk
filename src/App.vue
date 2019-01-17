<template>
  <div id="app">
   
    <div class="container mt-5">
      <div class="row">
        <div class="col-1"></div>
        <div class="col-10">
          <SearchForm v-on:formSubmitted="searchFromAPI" v-on:showLoading="loadingShow"/>  
          <ResultList v-bind:wordDefList="wordDef" />
          
          <div v-show="isLoading">
          <looping-rhombuses-spinner :animation-duration="2500" :rhombus-size="15" color="#ff1d5e" style="margin: 0 auto;" />
          </div>
        
        </div>
        <div class="col-1"></div>
      </div>
    </div>

   
  </div>
</template>

<script>

import SearchForm from './components/SearchForm'
import ResultList from './components/ResultList'
import axios from 'axios'
import {LoopingRhombusesSpinner} from 'epic-spinners/dist/lib/epic-spinners.min.js'
import 'epic-spinners/dist/lib/epic-spinners.min.css'

export default {
  name: 'app',
  components: {
    SearchForm,
    ResultList,
    LoopingRhombusesSpinner
  },
  methods: {
    searchFromAPI(val){
      axios.get('http://cevir.ws/v1?q='+ val.wordFrom +'&m=25&p=exact&l=' + this.langPairs[val.langPair])
      .then(res => this.wordDef = res.data.word);
    },
    loadingShow: function(){
      this.isLoading = true;
    }
  },
  data() {
    return {
      langPairs: {
        "Türkçe-İngilizce" : "tr",
        "İngilizce-Türkçe" : "en"
      },
      wordDef: '',
      isLoading: false
    }
  },
  watch: {
    wordDef: function(){
      this.isLoading = false;
    }
  }
}
</script>

<style>


</style>
