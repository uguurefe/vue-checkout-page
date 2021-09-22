<template>
  <div class="cart-list">
    <h2 class="cart-list__title">ALIŞVERİŞ SEPETİM</h2>
    <div class="cart-list__items">
      <div v-for="item in list" :key="item.ProductId">
        <CartItem :item="item"/>
      </div>
    </div>
  </div>
</template>

<script>
import CartItem from '../CartItem'
export default {
  name: 'CartItemList',
  components:{
    CartItem
  },
  props:{
    list:Array
  }
}
</script>
<style scoped lang="scss">
@import './styles.scss';
</style>