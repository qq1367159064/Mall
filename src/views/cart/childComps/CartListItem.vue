<template>
  <div id="shop-item">
    <div class="item-selector">
      <CheckButton :isCheck="itemInfo.checked" @click.native='checkClick'/>
    </div>
    <div class="item-img">
      <img :src="itemInfo.images" alt="商品图片" />
    </div>
    <div class="item-info">
      <div class="item-title">{{itemInfo.title}}</div>
      <div class="item-desc">商品描述: {{itemInfo.des}}</div>
      <div class="info-bottom">
        <div class="item-price left">¥{{itemInfo.prices}}</div>
        <div class="item-count right">x{{itemInfo.count}}</div>
      </div>
    </div>
  </div>
</template>

<script>
import CheckButton from "./CheckButton";

export default {
  name: "ShopCartItem",
  props: {
    itemInfo: Object
  },
  components: {
    CheckButton
  },
  methods: {
    checkedChange: function() {
      this.itemInfo.checked = !this.itemInfo.checked;
    },
    checkClick() {
      this.itemInfo.checked = !this.itemInfo.checked
    }
  }
};
</script>

<style lang="less" scoped>
  #shop-item {
    width: 100%;
    display: flex;
    font-size: 0;
    padding: 5px;
    border-bottom: 1px solid #ccc;

    .item-selector {
      width: 14%;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .item-img {
      padding: 5px;
      /*border: 1px solid #ccc;*/
      img {
        width: 80px;
        height: 100px;
        display: block;
        border-radius: 5px;
      }
    }

    .item-info {
      font-size: 17px;
      color: #333;
      padding: 5px 10px;
      position: relative;
      overflow: hidden;

      .item-title,
      .item-desc {
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
      }

      .item-desc {
        font-size: 14px;
        color: #666;
        margin-top: 15px;
      }

      .info-bottom {
        margin-top: 10px;
        position: absolute;
        bottom: 10px;
        left: 10px;
        right: 10px;

        .item-price {
          color: orangered;
        }
      }
    }
  }
</style>
