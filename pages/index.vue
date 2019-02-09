<template>
  <section class="container">
    <div>
      <h1 class="title">
        ga-ecommerce-test-nuxt
      </h1>
      <h2 class="subtitle">
        Nuxtを使ってGoogleアナリティクスの拡張eコマースをテストするためのレポジトリ
      </h2>
      <div class="links">
        <div
          class="button--green"
          @click="BeginCheckout()"
        >
          決済プロセスの開始
        </div>
        <div
          class="button--grey"
          @click="SetCheckoutOption1()"
        >
          配送方法の指定
        </div>
        <div
          class="button--grey"
          @click="SetCheckoutOption2()"
        >
          支払い方法の指定
        </div>
        <div
          class="button--green"
          @click="CheckoutProgress()"
        >
          決済プログレスの続き
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  components: {},
  methods: {
    BeginCheckout() {
      console.log(this.$gtag)
      this.$gtag('event', 'begin_checkout', {
        items: [
          {
            id: 'P12345',
            name: 'Android Warhol T-Shirt',
            list_name: 'Search Results',
            brand: 'Google',
            category: 'Apparel/T-Shirts',
            variant: 'Black',
            list_position: 1,
            quantity: 2,
            price: '2.0'
          }
        ],
        coupon: ''
      })
    },
    CheckoutProgress() {
      this.$gtag('event', 'checkout_progress', {
        items: [
          {
            id: 'P12345',
            name: 'Android Warhol T-Shirt',
            list_name: 'Search Results',
            brand: 'Google',
            category: 'Apparel/T-Shirts',
            variant: 'Black',
            list_position: 1,
            quantity: 2,
            price: '2.0'
          }
        ],
        coupon: 'SUMMER_DISCOUNT'
      })
    },
    SetCheckoutOption1() {
      this.$gtag('event', 'set_checkout_option', {
        checkout_step: 1,
        checkout_option: 'shipping method',
        value: 'USPS'
      })
    },
    SetCheckoutOption2() {
      this.$gtag('event', 'set_checkout_option', {
        checkout_step: 1,
        checkout_option: '支払い方法',
        value: 'VISA'
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
  font-weight: 300;
  font-size: 6vw;
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
}
</style>
