<template>
  <center><h1>kategori</h1></center>
  <center>
  <div class="flex-container">
      <div v-for="kategori in cek" :key="kategori.id" class="card">
        <img class="img" :src="img(kategori.img)" alt="Foto">
      <router-link class="container" :to="{ name : 'KategoriProduk', params:{id_kategori : kategori.id}}">
          <h4>{{ kategori.nama }}</h4>
      </router-link>
  </div>
  </div>
  </center>
</template>
<script>
import { onMounted, reactive } from 'vue';
import { kategori } from '@/assets/Kategori';

export default{
  setup(props,context){

      const cek = reactive(kategori["kategori"]);

      onMounted(() => {
          context.emit("id-menu",5)
      });

    const img = (NamaFoto) => {
      return '../src/assets/pictures/' + NamaFoto + '';
      }

      return{
        cek,
          img
      }
  }
}
</script>
<style scoped>

.card {
  box-shadow: 0 4px 8px 0 rgba(0,0, 0, 0.2);
  transition: 0.3s;
  margin: 10px;
  min-width: 200px;
  cursor: pointer;
  text-align: center;
}
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0, 0, 0.2);
}
.container {
  padding: 2px 16px;
}

.img{
  max-width: 190px;
  border: 1px solid #ddd;
    border-radius: 4px;
    padding: 5px;
  
  
}
</style>