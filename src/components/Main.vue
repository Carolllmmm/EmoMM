<script>
import Title from './sections/Title.vue'
import Abstract from './sections/Abstract.vue'
import Markdown from './sections/Markdown.vue'
import BibTeX from './sections/BibTeX.vue'
import Overview from './sections/Overview.vue'
import Benchmark from './sections/Benchmark.vue'
import Markdown from './sections/Markdown.vue'

export default {
  components: {
    Title,
    Abstract,
    BibTeX,
    Overview,
    Benchmark,
    Markdown
  }
}
</script>

<template>
  <Title/>
  <Abstract/>
  <Markdown/>
  <Overview/>
  <Benchmark/>
  <BibTeX/>
</template>
