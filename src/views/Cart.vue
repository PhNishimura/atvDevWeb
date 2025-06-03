<template>
    <main>
      <section class="cart-title-container">
        <h1>Seu Carrinho</h1>
        <p>Revise seus itens antes de finalizar a compra</p>
      </section>

      <section class="cart-container">
        <div class="cart-items">
          <div class="cart-empty" v-if="cartItems.length === 0">
            <i class="fas fa-shopping-cart"></i>
            <p>Seu carrinho está vazio</p>
          <router-link to="/products" class="button">Continuar Comprando</router-link>
          </div>
        </div>

        <div class="cart-summary">
          <h3>Resumo do Pedido</h3>
          <div class="summary-details">
            <div class="summary-row">
              <span>Subtotal</span>
              <span class="subtotal">R$ {{ subtotal.toFixed(2) }}</span>
            </div>
            <div class="summary-row">
              <span>Frete</span>
              <span class="shipping">R$ {{ shipping.toFixed(2) }}</span>
            </div>
            <div class="summary-row total">
              <span>Total</span>
              <span class="total-price">R$ {{ total.toFixed(2) }}</span>
            </div>
          </div>
          <router-link to="/thanks" class="checkout-button">Finalizar Compra</router-link>
          <router-link to="/products" class="continue-shopping">Continuar Comprando</router-link>
        </div>
      </section>
    </main>
</template>

<script setup>
import { ref, computed } from 'vue';

const theme = ref('theme-light');
const cartItems = ref([]); // Aqui você pode carregar com dados reais

const subtotal = computed(() => cartItems.value.reduce((acc, item) => acc + item.price * item.quantity, 0));
const shipping = ref(0); // Pode ser calculado ou fixo
const total = computed(() => subtotal.value + shipping.value);

function toggleTheme() {
  theme.value = theme.value === 'theme-light' ? 'theme-dark' : 'theme-light';
}
</script>

<style scoped>
</style>
