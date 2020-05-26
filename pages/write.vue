<template>
  <div class="">
    <notifications group="foo" />
    <div class="box container" style="margin-top: 3%">
      <form @submit.prevent="submit">
        <input
          type="text"
          class="inputs"
          placeholder="Title"
          style="margin-top: -5px;"
          v-model="title"
          required
        />
        <input
          type="email"
          class="inputs"
          placeholder="Lover email address"
          v-model="email"
          required
        />
        <input
          type="text"
          class="inputs"
          placeholder="Paying address (optional)"
          v-model="pay_address"
        />
        <textarea placeholder="Markdown body" v-model="source" required />
        <div style="display: block; margin-bottom: 50px;">
          <input type="checkbox" id="send" value="true" v-model="public_it" />
          <label for="send" style="color: #313131; padding-left: 5px;">
            Make it a public post?
          </label>
        </div>
        <div>
          <button class="custom-button">Preview</button>
          <button type="submit" class="custom-button">Submit</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: '',
      email: '',
      pay_address: '',
      public_it: false,
      source: ''
    }
  },
  methods: {
    async submit() {
      try {
        // get all posts from database
        let id = (await this.$fireDb.ref('/posts').once('value')).val()

        // if database is empty, the new id will be 1, else it will be the lenght of the array
        if (id === null) id = 1
        else id = id.length

        // set addMessage function from firebase
        const addMessage = this.$fireFunc.httpsCallable('sendEmail')

        // send the magic email
        const hatz = await addMessage({
          title: this.title,
          email: this.email,
          pay_address: this.pay_address,
          data: this.source
        })

        // handle response status
        if (hatz.data.status === 'ok') {
          this.$notify({
            group: 'foo',
            title: 'The email is fine!',
            type: 'success',
            text: 'Your email has been sent!'
          })

          // reset each parameter
          this.title = ''
          this.email = ''
          this.pay_address = ''
          this.source = false
        } else
          return this.$notify({
            group: 'foo',
            title: 'The email is :((',
            type: 'error',
            text:
              'Your email coudn"t be delivered :(\n Details: ' + hatz.data.err
          })

        // handle is public checkbox
        if (this.public_it) {
          // write the data into the database if the user wants to make it a public story and start receive payments

          await this.$fireDb.ref(`/posts/${id}`).set({
            title: this.title,
            email: this.email,
            pay_address: this.pay_address,
            data: this.source
          })

          // push user to the post page
          this.$router.push(`/posts/${id}`)
        }
      } catch (err) {
        if (err) alert(err)
      }
    }
  }
}
</script>

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
