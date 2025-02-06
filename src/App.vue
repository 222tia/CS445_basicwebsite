<script setup>
  import { reactive, ref } from 'vue';

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

</template>

<style scoped>

p {
  padding-top: 10px;
}

</style>
