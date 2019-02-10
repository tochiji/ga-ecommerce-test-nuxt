<template>
  <section class="container">
    <div>
      <h1 class="title">
        ga-ecommerce-test-nuxt
      </h1>
      <h2 class="subtitle">
        <div>Googleアナリティクスの「拡張eコマース/決済プロセス」テスト用</div>
        <div>テスト要件に合わせpages/index.vueやstore/index.jsを編集してください</div>
      </h2>
      <div class="links">
        <div
          class="button--green"
          @click="BeginCheckout()"
        >
          決済プロセスの開始
          <div>
            例：gtag('event', 'begin_checkout', { items: […],
            checkout_step: 1,
            coupon: ''})
          </div>
        </div>
        <div
          class="button--grey"
          @click="SetCheckoutOption1()"
        >
          配送方法の指定
          <div>
            例：gtag('event', 'set_checkout_option', {
            checkout_step: 1,
            checkout_option: 'shipping method',
            value: 'ヤマト クール便'
            })
          </div>
        </div>
        <div
          class="button--grey"
          @click="SetCheckoutOption2()"
        >
          支払い方法の指定
          <div>
            例：gtag('event', 'set_checkout_option', {
            checkout_step: 1,
            checkout_option: '支払い方法',
            value: 'クレジットカード VISA'
            })
          </div>
        </div>
        <div
          class="button--green"
          @click="CheckoutProgress()"
        >
          決済プログレスの続き
          <div>
            例：gtag('event', 'checkout_progress', {
            items: […],
            checkout_step: 2,
            coupon: 'SOME_COUPON'
            })
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { mapState } from 'vuex'

export default {
  components: {},
  computed: {
    ...mapState(['itemlist'])
  },
  methods: {
    BeginCheckout() {
      console.log('BeginCheckout : ' + JSON.stringify(this.itemlist[1]))
      this.$gtag('event', 'begin_checkout', {
        items: [this.itemlist[1]],
        checkout_step: 1,
        coupon: ''
      })
    },
    CheckoutProgress() {
      console.log('CheckoutProgress : ' + JSON.stringify(this.itemlist[1]))
      this.$gtag('event', 'checkout_progress', {
        items: [this.itemlist[1]],
        checkout_step: 2,
        coupon: 'SUMMER_DISCOUNT'
      })
    },
    SetCheckoutOption1() {
      this.$gtag('event', 'set_checkout_option', {
        checkout_step: 1,
        checkout_option: 'shipping method',
        value: 'USPS P201902101937'
      })
    },
    SetCheckoutOption2() {
      this.$gtag('event', 'set_checkout_option', {
        checkout_step: 1,
        checkout_option: '支払い方法',
        value: 'VISA P201902101937'
      })
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 400;
  font-size: 4vw;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 2vw;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
</style>
