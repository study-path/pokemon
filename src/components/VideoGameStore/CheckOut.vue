<template>
  <section class="showcase">
    <div class="nes-container with-title">
      <h3>Donkey Kong Country SNES $19.99</h3>
      <div class="img">
        <img src="" alt="" srcset="" />
      </div>
    </div>
  </section>
  <div class="nes-container with-title is-centered">
    <form @submit.prevent="handleSubmit">
      <fieldset :class="{ dis: loading }" class="fields">
        <div class="nes-field"></div>
        <div class="nes-field">
          <label for="name_field">Name</label>
          <input
            placeholder="Jane Doe"
            type="text"
            name="name"
            id="name_field"
            class="nes-input"
          />
        </div>
        <div class="nes-field">
          <label for="email_field">Email</label>
          <input
            placeholder="jane.doe@example.com "
            type="email"
            name="email"
            id="email_field"
            class="nes-input"
          />
        </div>
        <div class="nes-field">
          <label for="address_field">Address</label>
          <input
            placeholder="1234 Sycamore Street"
            type="text"
            name="address"
            id="address_field"
            class="nes-input"
          />
        </div>
        <div class="nes-field">
          <label for="city_field">City</label>
          <input
            placeholder="Reno"
            type="text"
            name="city"
            id="city_field"
            class="nes-input"
          />
        </div>
        <div class="nes-field">
          <label for="state_field">State</label>
          <input
            placeholder="Nevada"
            type="text"
            name="state"
            id="state_field"
            class="nes-input"
          />
        </div>
        <div class="nes-field">
          <label for="zip_field">Zip</label>
          <input
            placeholder="89523"
            type="text"
            name="zip"
            id="zip_field"
            class="nes-input"
          />
        </div>
        <div class="nes-field">
          <label for="email_field">Credit Card</label>
          <div id="stripe-element-mount-point" class="nes-input" />
        </div>
      </fieldset>
      <div class="nes-field">
        <button
          type="submit"
          class="nes-btn is-primary"
          :class="{ dis: loading }"
        >
          {{ loading ? "Loading..." : "Pay $19.99" }}
        </button>
      </div>
    </form>
  </div>
  <h2>Or...</h2>
  <div class="nes-field mt">
    <button type="button" class="nes-btn is-success" @click="redirect">
      Pay $19.99 Page
    </button>
  </div>
</template>

<script>
import { onMounted } from "@vue/runtime-core";
import { loadStripe } from "@stripe/stripe-js";
export default {
  setup() {
    let stripe = null;

    onMounted(async () => {
      stripe = await loadStripe(
        "pk_test_51LstIKFSfCGayDoFRebzfNz0TZ1BON7AdBlgyAJ9wgiP9JqdOHsmMHpfQxSiv7IB5s0Fwa95xn1roM4ds1g0IzcR00m92bovRZ"
      );
    });

    function redirect() {
      console.log("stripe:", stripe);
      stripe.redirectToCheckout({
        successUrl: "http://localhost:8080/successResult",
        cancelUrl: "http://localhost:8080/videoGameStore",
        lineItems: [
          {
            price: "price_1LstJNFSfCGayDoFMQ5ra9Dj",
            quantity: 1,
          },
        ],
        mode: "payment",
      });
    }
    return { redirect };
  },
};
</script>

<style scoped>
.checkout {
  border: 1px solid black;
  padding: 3px;
}
.fields {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  gap: 30px;
}
.img {
  display: flex;
  justify-content: center;
}
.showcase {
  margin-bottom: 20px;
}
.mt {
  margin-top: 20px;
}
.dis {
  opacity: 0.5;
  cursor: default;
  pointer-events: none;
}
button {
  margin-top: 30px;
}
</style>
