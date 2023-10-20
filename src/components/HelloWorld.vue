<script setup>
import { ref, computed } from "vue";
import { marked } from "marked";
import prism from "prismjs";

const mdfile = "/README.md";
const markDown = ref("");

const getMarkdownData = async () => {
  await fetch(mdfile)
    .then((response) => response.text())
    .then((data) => (markDown.value = data));
};
const mdToHtml = computed(() => {
  const mdhtml = marked.parse(markDown.value);
  return mdhtml;
});

getMarkdownData()
</script>

<template>
  <div v-html="mdToHtml"></div>
</template>

<style scoped>
h1 {
    font-weight: 500;
    font-size: 2.6rem;
}
h2 {
    margin-top: 15px;
}
h3 {
    margin-top: 10px;
    font-size: 1.2rem;
}
</style>
