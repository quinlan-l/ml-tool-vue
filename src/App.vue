<template>
  <div class="sc-flex-box">

    <select class="sc-select" v-if="sites.length" v-model="siteIdx" @change="siteChanged">
      <option v-for="(site, idx) in sites" :value="idx"> {{ site.name }} </option>
    </select>
    <div class="sc-input-wrapper">
      <input class="sc-input" autofocus="true" :placeholder="prompt" v-model="keyword" @keyup.enter="searchOrNot">
      <span id="sc-input_right" @click="searchOrNot"></span>
    </div>

  </div>
</template>

<script setup lang="ts">
import { ref } from "vue"
const sites = ref([
  {
    "name": "Google",
    "host": "www.google.com",
    "url": "https://www.google.com/search?q="
  },
  {
    "name": "搜狗",
    "host": "www.sogou.com",
    "url": "https://www.sogou.com/web?query="
  },
  {
    "name": "Bing",
    "host": "www.bing.com",
    "url": "https://www.bing.com/search?q="
  },
  {
    "name": "百度",
    "host": "www.baidu.com",
    "url": "https://www.baidu.com/s?wd="
  },
  {
    "name": "Wikipedia镜像",
    "host": "emw.1369.ml",
    "url": "https://emw.1369.ml/w/index.php?search="
  },
  {
    "name": "维基百科镜像",
    "host": "zmw.1369.ml",
    "url": "https://zmw.1369.ml/w/index.php?search="
  },
  {
    "name": "知乎",
    "host": "搜狗·知乎",
    "url": "https://www.sogou.com/sogou?insite=zhihu.com&query="
  },
  {
    "name": "微信",
    "host": "搜狗·微信",
    "url": "https://weixin.sogou.com/weixin?type=2&query="
  },
  {
    "name": "豆瓣",
    "host": "www.douban.com",
    "url": "https://www.douban.com/search?q="
  },
  {
    "name": "Stack Overflow",
    "host": "stackoverflow.com",
    "url": "https://stackoverflow.com/search?q="
  },
  {
    "name": "Zlibrary镜像",
    "host": "zl.1369.ml",
    "url": "https://zl.1369.ml/s/"
  }
])
const siteIdx = ref(2)
var prompt = ref(genPrompt(siteIdx.value))
const keyword = ref("")

function siteChanged(event) {
  if (event) {
    if (keyword.value == "") {
      prompt.value = genPrompt(event.target.value)
    } else {
      search()
    }
  }
}

function searchOrNot() {
  if (keyword.value != "") {
    search()
  }
}

function genPrompt(idx: number) {
  return "在 " + sites.value[idx].host + " 中搜索"
}
function search() {
  var idx = siteIdx.value
  var targetSite = sites.value[idx].url
  window.open(targetSite + keyword.value)
}
</script>

<style scoped lang="scss">
.sc-flex-box {
  display: flex;
  flex-direction: column;
  width: 500px;
  height: 130px;
  justify-content: space-between;
  align-items: center;
}


$sc-box-height : 52px;

.sc-input-wrapper {
  width: 100%;
}

.sc-input {
  width: 100%;
  height: $sc-box-height;
  padding: 0 52px;
  box-sizing: border-box;
  border-radius: 26px;
  font-size: 18px;
  color: #2196f3;
  text-align: center;
}

.sc-select {
  width: 80%;
  height: $sc-box-height;
  font-size: 16px;
  color: #2196f3;
  border: 0;
  text-align: center;
}
</style>