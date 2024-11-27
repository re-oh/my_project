<script setup>
import { ref } from 'vue';
import { my_project_backend } from 'declarations/my_project_backend/index';
let chat = ref([]);

async function getChat() {
  chat.value = await my_project_backend.get_chat()
}

async function handleSubmit(e) {
  e.preventDefault();
  const target = e.target;
  const msg = target.querySelector('#name').value;
  await my_project_backend.add_msg(msg);
  getChat();
}
</script>

<template>
  <main>
    <img src="/logo2.svg" alt="DFINITY logo" />
    <br />
    <br />
    <form action="#" @submit="handleSubmit">
      <label for="name">Enter your msg: &nbsp;</label>
      <input id="name" alt="Name" type="text" />
      <button type="submit">Click Me!</button>
    </form>
    <section id="greeting">{{ greeting }}</section>
  </main>
</template>
