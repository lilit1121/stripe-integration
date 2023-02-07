<template>
  <div class="page">
    <div class="mb-5">
        <h1 class="text-center payment-heading">Test payment integration with Stripe</h1>
        <h5 class="mt-3 payment-content">More information can be found on the website. <a class="link" href="https://stripe.com/docs" target="_blank">Stripe</a></h5>
    </div>
    <stripe-checkout
      ref="checkoutRef"
      mode="payment"
      :pk="publishableKey"
      :line-items="lineItems"
      :success-url="successURL"
      :cancel-url="cancelURL"
      @loading="v => loading = v"
    />
    <div class="d-flex justify-content-center">
        <b-button variant="info" class="blue-btn w-100" @click="submit">Pay now</b-button>
    </div>
  </div>
</template>

<style scoped>
    .payment-heading{
        color: #484d4e;
        font-size: 30px;
    }
    .payment-content{
        text-align: center;
        font-size: 16px;
    }
    .link{
        color: #138496;
    }
    .link:hover{
        text-decoration: none;
        color: #138496;
    }
    @media only screen and (max-width: 600px) {
        .payment-heading{
            font-size: 25px;
        }
        .payment-content{
            text-align: left;
            font-size: 15px;
        }
    }
</style>

<script>
import { StripeCheckout } from '@vue-stripe/vue-stripe';
export default {
  components: {
    StripeCheckout,
  },
  data () {
    this.publishableKey = 'pk_test_51M7CaeGtTze3yvcZ8AH6s41UryxSUfMDGSHA27dLjWGmZtjZvqCEiPk0nzrsjSLPZoZWrkjdVQharUe6MRqCe77x00oCwm3hKC';
    return {
      loading: false,
      lineItems: [
        {
          price: 'price_1M7CmeGtTze3yvcZVVTiyLcg',
          quantity: 1,
        },
      ],
      successURL: 'http://localhost:8080/payment',
      cancelURL: 'http://localhost:8080/payment',
    };
  },
  methods: {
    submit () {
      this.$refs.checkoutRef.redirectToCheckout();
    },
  },
};
</script>