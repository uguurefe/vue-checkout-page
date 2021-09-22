<template>
    <div class="row cart-item">
        <div class="col-md-2 cart-item__img">
            <img :src='item.ResizedImage' alt="item">
        </div>
        <div class="col-md-9 cart-item__detail">
            <div class="cart-item__brand"><h3>{{item.Brand}}</h3></div>
            <div class="cart-item__description">{{item.DisplayName}}</div>
            <div class="cart-item__price">
                <div class="cart-item__discount">-%{{item.DiscountRate}}</div>
                <div class="cart-item__prices">
                    <div class="cart-item__old-price">{{item.OriginalPrice}} TL</div>
                    <div class="cart-item__new-price">{{item.SalePrice}} TL</div>
                </div>
            </div>
            <div class="cart-item__color"><span>Renk</span> {{item.Color}}</div>
            <div class="cart-item__size"><span>Beden</span> {{item.Size}}</div>
            <div class="cart-item__quantity">
                <span>Adet</span> 
                <select v-model="item.Quantity" v-on:change="updateItem">
                    <option :value="1">1 adet</option>
                    <option :value="2">2 adet</option>
                </select>
            </div>
        </div>
        <div class="col-md-1 cart-item__btn">
            <button v-on:click="deleteItem">Sil</button>
        </div>
    </div>
</template>

<script>
export default {
  name: 'CartItem',
  props:{
      item:Object
  },
  methods:{
    deleteItem(){
        this.$parent.$parent.removeItem(this.item.id);
    },
    updateItem(e){
        if(e.target.options.selectedIndex > -1) {
           const selectVal=e.target.options[e.target.options.selectedIndex].value;
           this.$parent.$parent.updateItem(this.item.id,selectVal);
        }
    },
  }
}
</script>
<style scoped lang="scss">
 @import './styles.scss';
</style>