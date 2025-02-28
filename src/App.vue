<script setup>
  import { reactive, ref } from 'vue';

  import seacreature1 from '@/assets/seacreature1.jpg';
  import seacreature2 from '@/assets/seacreature2.jpg';
  import seacreature3 from '@/assets/seacreature3.jpg';
  import seacreature4 from '@/assets/seacreature4.jpg';
  import seacreature5 from '@/assets/seacreature5.jpg';
  import seacreature6 from '@/assets/seacreature6.jpg';

  const items = reactive([
    { name: "kewpie mayo", count: 0 },
    { name: "furikake", count: 0 },
    { name: "nori", count: 0 }
  ]);

  const message = ref("");

  function increase(index) {
    items[index].count++;
  };

  function decrease(index) {
    if (items[index].count > 0) {
      items[index].count--;
    }
  };

  function showMessage() {
    const messages = ["Order placed!", 
                      "Thank you for your order!", 
                      "No."];
    const random = Math.floor(Math.random() * messages.length);
    message.value = messages[random];
  }

</script>

<template>
<div>

<div>
  <div>
    <h1>Add to Order</h1> 
  </div>

  <div>
    <div v-for="(item, index) in items" :key="item.name">
      <p>{{ item.name }} 
        <button @click="decrease(index)">-</button>
        <button @click="increase(index)">+</button> 
        : {{ item.count }}</p>
    </div>
    <div style="padding-top:10px">
      <button @click="showMessage">order</button>
      <p>{{ message }}</p>
    </div>
  </div>
</div>

  <div class="gallery">
    <h1>Gallery of Cute Sea Creatures</h1>
      <div class="gallery-grid">
        <img :src="seacreature1" alt="Sea Creature 1">
        <img :src="seacreature2" alt="Sea Creature 2">
        <img :src="seacreature3" alt="Sea Creature 3">
        <img :src="seacreature4" alt="Sea Creature 4">
        <img :src="seacreature5" alt="Sea Creature 5">
        <img :src="seacreature6" alt="Sea Creature 6">
      </div>
  </div>

</div>
</template>

<style scoped>

p {
  padding-top: 10px;
}

.gallery {
  margin-top: 20px;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
  max-width: 450px;
}

img {
  width: 100%;
  aspect-ratio: 1 / 1;
  object-fit: cover;
  border-radius: 8px;
}

</style>
