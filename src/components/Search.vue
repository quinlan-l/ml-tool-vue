
<template>
 
    <select class="search_select"  v-if="sites.length" v-model="selectedIdx" @select="event => inputPromt=event.target.value">
    <option v-for="(site, idx) in sites" :value="idx"> {{ site.name }} </option>
  </select>
  <div class="input_wrapper">
    {{ inputPrompt }}
  <input class="search_input" autofocus="autofocus" autocomplete="off" :placeholder="inputPrompt" v-model="searchKeyword" @keyup.enter="goSearch">
  <span id="search_input_right" @click="goSearch"></span>

  </div>
  
</template>

<script setup lang="ts">
  import { ref } from "vue"
  const sites = ref([
    {
      "name": "Google", 
      "url": "https://www.google.com/search?q="
    }, 
    {
      "name": "搜狗", 
      "url": "https://www.sogou.com/web?query="
    }, 
    {
      "name": "Bing", 
      "url": "https://www.bing.com/search?q="
    }, 
    {
      "name": "百度", 
      "url": "https://www.baidu.com/s?wd="
    }, 
    {
      "name": "Wikipedia镜像", 
      "url": "https://emw.1369.ml/w/index.php?search="
    }, 
    {
      "name": "维基百科镜像", 
      "url": "https://zmw.1369.ml/w/index.php?search="
    }, 
    {
      "name": "知乎", 
      "url": "https://www.sogou.com/sogou?insite=zhihu.com&query="
    }, 
    {
      "name": "微信", 
      "url": "https://weixin.sogou.com/weixin?type=2&query="
    }, 
    {
      "name": "豆瓣", 
      "url": "https://www.douban.com/search?q="
    }, 
    {
      "name": "Stack Overflow", 
      "url": "https://stackoverflow.com/search?q="
    }, 
    {
      "name": "Zlibrary镜像", 
      "url": "https://zl.1369.ml/s/"
    }
  ])
  const selectedIdx = ref(2)
  const inputPrompt = ref("在 " + sites.value[selectedIdx.value].name + " 中搜索")
  const searchKeyword = ref("")

  function goSearch() {
    if(searchKeyword.value != "") {
      var idx = selectedIdx.value
      var targetSite = sites.value[idx].url
      window.open(targetSite + searchKeyword.value)
    }
  }
</script>

<style>
:root{
  --ntp-search-box-width : 561px;
  --ntp-search-box-height : 44px;
  --ntp-realbox-border-radius: calc(0.5 * var(--ntp-search-box-height));
}

.search_input {
  width: var(--ntp-search-box-width);
  height: var(--ntp-search-box-height);
  border-radius: var(--ntp-realbox-border-radius);
}

</style>