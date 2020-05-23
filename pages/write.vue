<template>
  <div class="container">
    <textarea v-model="source" />
    <vue-simple-markdown :source="source"> </vue-simple-markdown>
  </div>
</template>

<script>
export default {
  layout: 'default',
  data() {
    return {
      source: '```sdasdas```'
    }
  }
}
</script>
