<template>
  <div class="cart-summary">
    <div class="cart-summary__top">
        <h2 class="cart-summary__heading">SEPET ÖZETİ</h2>
    </div>
    <div class="cart-summary__body">
        <div class="row cart-summary__list">
            <div class="cart-summary__title col-8 col-md-8">Toplam Tutar (KDV Dahil)</div>
            <div class="cart-summary__value col-4 col-md-4">{{summary.TotalAmount}} TL</div>
            <div class="cart-summary__title col-8 col-md-8" v-if="summary.DiscountAmount">Etiket İndirimi</div>
            <div class="cart-summary__value col-4 col-md-4" v-if="summary.DiscountAmount">-{{summary.DiscountAmount}} TL</div>
            <div class="cart-summary__title col-8 col-md-8" v-if="summary.CouponDiscountAmount">Kupon İndirimi</div>
            <div class="cart-summary__value col-4 col-md-4" v-if="summary.CouponDiscountAmount">{{summary.CouponDiscountAmount}} TL</div>
            <div class="cart-summary__title col-8 col-md-8">Kargo Ücreti</div>
            <div class="cart-summary__value col-4 col-md-4">{{summary.CargoAmount}} TL</div>
        </div>
    </div>
    <div class="cart-summary__footer">
        <div class="row cart-summary__list">
            <div class="cart-summary__title col-8 col-md-8">Ödenecek Tutar</div>
            <div class="cart-summary__value col-4 col-md-4">{{summary.GeneralTotalAmount}} TL</div>  
        </div>
        <button class="cart-summary__button">DEVAM ET</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CartSummary',
  props:{
    summary: Object,
  }
}
</script>
<style scoped lang="scss">
 @import './styles.scss';
</style>