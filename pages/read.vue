<template>
  <div class="">
    <div
      class="box"
      style="margin: auto; margin-top: 20px; width: 50%;"
      v-for="item in data"
      :key="item.lenght"
    >
      <div>
        <span class="title"> {{ capitalize(item.title) }}</span>
      </div>
      <span class="line"></span>
      <div>
        <span class="description"> {{ item.data }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: []
    }
  },
  async created() {
    // get data from database
    this.data = (await this.$fireDb.ref('/posts').once('value')).val()

    // filter undefined elements
    if (this.data)
      this.data = this.data.filter((Element) => Element != undefined)
  },
  methods: {
    capitalize(s) {
      if (typeof s !== 'string') return ''
      return s.charAt(0).toUpperCase() + s.slice(1)
    }
  }
}
</script>

<style scoped>
.box {
  display: grid;
}

.title {
  color: #313131;
}

.line {
  width: 100%;
  float: center;
  margin-top: 20px;
  margin-bottom: 20px;
  border-bottom: solid #e6e6e6 1px;
}

.description {
  font-family: 'Roboto', sans-serif;
  font-size: 15px;
  color: #313131;
}
</style>
