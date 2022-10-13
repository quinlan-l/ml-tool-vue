<template>
<h2>Vue Demo</h2>

<h3>1. hello，world</h3>

<p> {{ message }} </p>

<h3>2. handle message</h3>

<p> {{ msg }} </p>

<button @click=reverseMsg> Reverse Msg </button>

<button @click="msg += '!'"> Append ! </button>

<a href="https://www.baidu.com" @click.prevent="notify"> click me get a notify not a redirect </a>

<h3>3. attribute bind</h3>

<span :title="message"> hover mouse to me. </span>

<p :class="{ red: isRed }" @click="toggleRed"> click this line can toggle it's color. {{ isRed }} </p>

<span :style="{ color: color }" @click="toggelColor"> click this line can toggle it's color. {{ color }} </span>

<h3>4. condition and foreach</h3>

<ul v-if = "isShow && list.length">
  <li v-for = "item in list"> {{ item }} </li>
</ul>
<p v-else-if = "list.length"> list still exist, but hidden. </p>
<p v-else> list is empty </p>

<button @click = "toggleList"> toggle list </button>
<button @click = "list.push(list.length + 1)" > push number </button>
<button @click = "list.pop()" > pop number </button>
<button @click = "list.reverse()" > reverse list </button>

<h3>5. Form bind</h3>

<h4>Text input</h4>

<input v-model="text"/> {{ text }}

<h4>Checkbox</h4>

<input type="checkbox" id="checkbox1" v-model="isCheck"/> 
<label for="checkbox1"> Checked: {{ isCheck }} </label>

<h4>Multi Checkbox</h4>

<input type="checkbox" id="apple" value="apple1" v-model="checkboxList"/><label for="apple"> 1.apple </label>
<input type="checkbox" id="banana" value="banana2" v-model="checkboxList"/><label for="banana"> 1.banana </label>
<input type="checkbox" id="cat" value="cat3" v-model="checkboxList"/><label for="cat"> 1.cat </label>

<p> {{ checkboxList }} </p>

<h4>Radio</h4>

<input type="radio" id="one" value="One" v-model="picked"><label for="one"> pick one. </label>

<input type="radio" id="two" value="Two" v-model="picked"><label for="two"> pick two. </label>

<input type="radio" id="three" value="Three" v-model="picked"><label for="three"> pick three. </label>

<p> I picked ... {{picked}} </p>

<h4>Select</h4>

<select v-model="selected">
  <option disabled> disable option </option>
  <option v-for="i in options"> {{ i }} </option>
</select>

<span> Selected {{ selected }} </span>

<h4>Multi Select</h4>

<select v-model="multiSelected" multiple>
  <option disabled> disable option </option>
  <option v-for="i in options"> {{ i }} </option>
</select>

<span> Selected {{ multiSelected }} </span>
</template>
<script setup>
  import { ref } from "vue"

  // case 1.
  const message = "this is a message"


  // case 2.
  const msg = ref("another message")
  function reverseMsg() {
    msg.value = msg.value.split('').reverse().join('')
  }

  function notify(){
    alert("this is a notify");
  }


  // case 3.
  const isRed = ref(true)
  function toggleRed() {
    isRed.value = !isRed.value
  }

  const color = ref("green")
  function toggelColor() {
    color.value = color.value == "green" ? "blue" : "green"
  }

  
  // case 4.
  const isShow = ref(true)
  const list = ref([1, 2, 3])
  
  function toggleList() {
    isShow.value = !isShow.value
  }

  // case 5.
  const text = ref("Edit me")
  const isCheck = ref(false)
  const checkboxList = ref(['cat3'])
  const picked = ref("")
  const options = ref(['a','b','c'])
  const selected = ref('b')
  const multiSelected = ref(['c'])
</script>

<style>
  .red {
    color: red;
  }
</style>