<script setup>
import { computed } from "vue";
const props = defineProps(["books"]);
const booksRead = computed(() => {
    return props.books.filter((book) => book.isRead).length;
});
const booksReadMessage = computed(() => {
    return booksRead.value >= props.books.length
        ? "Parabens! Você leu todos os seus livros!"
        : `${booksRead.value} de ${props.books.length} livros`;
});
</script>

<template>
    <div class="books-read">
        <label for="" class="progress">Seu progresso</label>
        <br />
        <progress :value="booksRead" :max="books.length"></progress>
        <p>{{ booksReadMessage }}</p>
    </div>
</template>
