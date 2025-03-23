<script setup>
import {
  ref,
  computed,
  reactive,
  watch,
  onMounted,
  onUnmounted,
  onUpdated,
} from "vue";

console.info("Hello Vue");

const hello = ref("Hello sobat coding");
const userInput = ref("");
const tes = ref("coba disini tes");
const warna = ref("yellow");
const tebal = ref("bold");

const daftar_lagu = ref([
  { judul: "Masing-Masing", tahun: 2020 },
  { judul: "Ayam Putih Pungguk", tahun: 2005 },
  { judul: "Mars Rokan Hilir", tahun: 2000 },
]);

const Nama_User = ref("");
const alert = computed(() => {
  console.log("fungsi alert di gunakan");
  return `Halo ${Nama_User.value}`;
});

const counter = ref(0);
const count = () => {
  counter.value++;
  console.log("fungsi count di gunakan");
};

const obj = reactive({ count: 0 });
function tambah() {
  obj.count++;
}

watch(
  () => obj.count,
  (newValue, oldValue) => {
    console.log("obj.count changed:", newValue, oldValue);
  }
);

import { useTemplateRef } from "vue";
const TemplateRef = useTemplateRef("input-tes");

function tampilkan() {
  console.log(ambil_nilai.value.value++);
}

onMounted(() => {
  console.log("Ini komponen mounted");
});

onUnmounted(() => {
  console.log("Ini komponen onUnmounted");
});

onUpdated(() => {
  console.log("Ini komponen onUpdate");
});
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

  <hr />
  <h1>Daftar Lagu</h1>
  <ul>
    <li v-for="item in daftar_lagu" :key="item.judul">
      {{ item.judul }}tahun{{ item.tahun }}
    </li>
  </ul>

  <input v-model="Nama_User" type="text" placeholder="Nama Kamu" />
  <h2>{{ alert }}</h2>
  <br />

  <button @click="count">Count is {{ counter }}</button>

  <button @click="tambah">Tambah Nilai</button>
  <p>Nilai nya:{{ obj.count }}</p>

  <h1>TESS TEMPLATE NYA</h1>
  <input ref="input-tes" />
  <button @click="tampilkan">Tampilkan</button>
</template>
