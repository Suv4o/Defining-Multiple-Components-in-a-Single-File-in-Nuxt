<script setup lang="ts">
const props = defineProps<{
    src: string;
}>();
</script>

<template>
    <img class="mx-auto h-48 w-48 rounded-full md:h-56 md:w-56" :src="props.src" alt="card image" />
</template>
