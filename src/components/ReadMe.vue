<script setup>
import { ref, computed } from "vue";
import { marked } from "marked";
import prism from "prismjs";

const mdfile = "https://raw.githubusercontent.com/Sebastix/necho/master/README.md";
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
  <div>
    <div v-html="mdToHtml" class="markdownContent">

    </div>
  </div>
</template>

<style scoped lang="postcss">
.markdownContent p {
  font-size: 16px;
}
</style>
