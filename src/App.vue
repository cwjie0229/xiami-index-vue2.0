<template>
  <div id="app">   
    <TopBar></TopBar>
    <TopHeader></TopHeader>
    <TopBanner></TopBanner>
    <top-sub></top-sub>
    <goods></goods>
    <Video  v-on:play='recivePlayVideo'></Video>
    <TempFooter></TempFooter>
    <PlayVideo  v-on:play='recivePlayVideo' :play-config="playConfig"></PlayVideo> 
  </div>
</template>
<script>
import TopBar from './components/TopBar'
import TopHeader from './components/TopHeader'
import TopBanner from './components/TopBanner'
import TopSub from './components/TopSub'
import Goods from './components/Goods'
import TempFooter from './components/TempFooter'
import PlayVideo from './components/common/PlayVideo'
import Video from './components/Video'
export default {
  data () {
    return {
      playConfig: {}
    }
  },
  mounted:function(){
  },
  methods: {
    recivePlayVideo (opts) {
        this.playConfig = opts
    }
  },
  components: {
    TopBar,TopHeader,TopBanner,TopSub,Goods,TempFooter,PlayVideo,Video
  }
}
</script>
<style>
@import './assets/css/base.css';
</style>
