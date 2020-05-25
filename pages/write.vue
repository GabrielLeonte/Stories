<template>
  <div class="container">
    <div class="box" style="margin-top: 3%">
      <input
        type="text"
        class="inputs"
        placeholder="Title"
        style="margin-top: -5px;"
        v-model="title"
      />
      <input
        type="email"
        class="inputs"
        placeholder="Lover email address"
        v-model="email"
      />
      <input
        type="text"
        class="inputs"
        placeholder="Paying address (optional)"
        v-model="pay_address"
      />
      <textarea placeholder="Markdown body" v-model="source" />
      <div style="display: block; margin-bottom: 50px;">
        <input type="checkbox" id="send" value="true" />
        <label for="send">Make it a public post? </label>
      </div>
      <div>
        <button class="custom-button">Preview</button>
        <button class="custom-button">Submit</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.inputs {
  width: 100%;
  margin-top: 10px;
  color: #313131;
  font-size: 20px;
  border: 0;
  padding-bottom: 5px;
  outline: none;
  user-select: none;
}

textarea {
  margin-top: 20px;
  resize: none;
  width: 100%;
  height: 400px;
  border: 0;
  outline: none;
  user-select: none;
  font-size: 14px;
}

.custom-button {
  margin: 0 auto;
  user-select: none;
  outline: none;
  position: relative;
  border: 0;
  background: #292929;
  color: #ffffff;
  font-family: 'Thasadith', sans-serif;
  font-size: 15px;
  border-radius: 5px;
  padding: 8px 15px 8px 15px;
}

.custom-button:hover {
  background: #151515;
}
</style>

<script>
export default {
  layout: 'default',
  data() {
    return {
      title: '',
      email: '',
      pay_address: '',
      source: ''
    }
  },
  async mounted() {
    try {
      await this.$fireDb.ref('/posts/2').set({
        data: 'hi',
        email: 'hsahdasjas',
        pay_address: 'oke'
      })

      const data = await this.$fireDb.ref('/posts').once('value')
      console.log(data.val())
    } catch (err) {
      if (err) alert(err)
    }
  }
}
</script>
