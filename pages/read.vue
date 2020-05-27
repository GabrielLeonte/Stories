<template>
  <div class="">
    <div
      class="box"
      style="margin: auto; margin-top: 20px; width: 50%;"
      v-for="item in data"
      :key="item.lenght"
    >
      <div style="display: grid;">
        <span class="title"> {{ capitalize(item.title) }}</span>
        <span class="subtitle" v-if="item.earned">
          Earned: {{ (item.earned * Math.pow(10, -9)).toFixed(9) }}$
        </span>
      </div>
      <span class="line"></span>
      <div>
        <div v-if="item.pay_address">
          <span class="description" v-if="isMonetized"> {{ item.data }}</span>
          <span v-else>
            This is premium content, to get access you must have a web
            monetization subscription <br />
            Learn More <a href="https://coil.com/"> Here </a>
          </span>
        </div>
        <div v-else>
          <span class="description"> {{ item.data }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'readpage',
  metaInfo() {
    return {
      title: 'Stories',
      meta: [
        {
          name: 'description',
          content:
            'Stories is a simple way to send an anonymous love letter, and get paid for it'
        },
        {
          property: 'og:title',
          content: 'Stories - Its time to love more'
        },
        { property: 'og:site_name', content: 'Stories' },
        {
          name: 'monetization',
          content: this.currentAddress
        }
      ]
    }
  },
  data() {
    return {
      data: [],
      monetizedContent: [],
      currentAddress: '',
      isLoading: false,
      isMonetized: false
    }
  },
  async created() {
    // get data from database
    this.data = (await this.$fireDb.ref('/posts').once('value')).val()

    if (this.data) {
      // filter undefined elements
      this.data = this.data.filter((Element) => Element != undefined)

      // get the latest post first
      this.data = this.data.reverse()

      this.data.forEach((element) => {
        if (element.pay_address.length > 10) this.monetizedContent.push(element)
      })

      this.currentAddress = this.monetizedContent[0].pay_address
    }
  },
  mounted() {
    if (!document.monetization) {
      // No web monetization polyfill is installed (e.g. Coil).
      this.isMonetized = false
      return
    }
    // Check the value of document.monetization.state
    // to see if a user is web monetized.
    const { state } = document.monetization

    if (state === 'stopped') {
      // Not currently sending micropayments, nor trying to.
      this.isMonetized = false
    }

    // Determine when Web Monetization has started actively paying
    document.monetization.addEventListener('monetizationstart', (event) => {
      this.isMonetized = true
    })

    // handle Coil Paying
    document.monetization.addEventListener(
      'monetizationprogress',
      async (event) => {
        event = event.detail

        // get current paying post array
        const post_data_array = this.monetizedContent.find(
          (element) => element.pay_address === event.paymentPointer
        )

        // get current paying post data from database
        const latest_post_data_array = (
          await this.$fireDb.ref(`/posts/${post_data_array.id}`).once('value')
        ).val()

        // update firebase database
        await this.$fireDb.ref(`/posts/${post_data_array.id}`).update({
          earned: Math.floor(
            latest_post_data_array.earned + Number(event.amount)
          )
        })

        // get current paying addrest post position in monetizedContent
        const post_data_array_position = this.monetizedContent.indexOf(
          post_data_array
        )

        // realtime client update to earned for each paid post
        this.monetizedContent[post_data_array_position].earned =
          this.monetizedContent[post_data_array_position].earned +
          Number(event.amount)

        // cycle through each address and again (everyone will receive one payment per iteration)
        if (post_data_array_position < this.monetizedContent.length - 1) {
          this.currentAddress = this.monetizedContent[
            post_data_array_position + 1
          ].pay_address
        } else if (
          post_data_array_position ===
          this.monetizedContent.length - 1
        )
          this.currentAddress = this.monetizedContent[0].pay_address
      }
    )
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
  margin-top: 10px;
  margin-bottom: 10px;
  border-bottom: solid #e6e6e6 1px;
}

.description {
  font-family: 'Roboto', sans-serif;
  font-size: 15px;
  color: #313131;
}

.subtitle {
  margin-left: 3px;
  font-size: 15px;
}
</style>
