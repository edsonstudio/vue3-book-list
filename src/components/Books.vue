<script setup>
const props = defineProps(["books"]);

// Ao utilizar event emits é necessário declará-los:
defineEmits(["toggleIsRead"]);
</script>

<template>
  <div class="books-list">
    <div v-for="book in books" :key="book.isbn" class="book">
      <div class="readIt" v-if="book.isRead">
        <i class="fa-solid fa-eye"></i>
      </div>
      <div class="book-cover">
        <img :src="book.cover" />

        <!-- Botão emitindo evento para o componente pai -->
        <button
          @click="$emit('toggleIsRead', book.id)"
          :class="{ isRead: book.isRead }"
        >
          <i class="fa-solid fa-eye"></i>
          <span>{{ book.isRead ? "Já li" : "Ainda não li" }}</span>
        </button>
      </div>
      <div class="book-details">
        <p class="book-author">{{ book.author }}</p>
        <h3 class="book-title">{{ book.title }}</h3>
        <p><i class="fa-solid fa-hashtag icon"></i>{{ book.isbn }}</p>
      </div>
    </div>
  </div>
</template>
