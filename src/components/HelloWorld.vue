<script setup>
import { ref } from "vue";

console.info("Hello Vue");

const hello = ref("Hello sobat coding");
const userInput = ref("");
const tes = ref("coba disini tes");
const warna = ref("yellow");
const tebal = ref("bold");
</script>

<template>
  <h1 class="hello">{{ hello }}</h1>
  <div v-html="hello"></div>
  <input v-model="userInput" type="text" placeholder="Masukan Nama Kamu 😁" />
  <input type="text" v-model="umurKamu" placeholder="Masukan umur kamu 😀" />
  <div>
    <p>Umur kamu 😊: {{ umurKamu }}</p>
    <p v-if="umurKamu < 15">Kamu masih kecik</p>
    <p v-else-if="umurKamu >= 15 && umurKamu < 50">Kamu dah besarr</p>
    <p v-else>Kamuu sudah tuaa</p>
  </div>
  <p>Nama yang kamu masukan: {{ userInput }}</p>
  <div>{{ tes }}</div>
  <button @click="() => (tes = 'Test telah berjaya!!')">Coba tukar</button>

  <div :style="{ color: warna, 'font-weight': tebal }">
    {{ userInput }}, {{ umurKamu }}
  </div>
</template>
