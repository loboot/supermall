<template>
  <div class="goods-item" @click="itemClick">
    <!-- <img :src="getImg" alt="" @load="imageLoad" /> -->
    <img  v-lazy="getImg" :key="getImg">
    <div class="goods-info">
      <p>{{ goodsItem.title }}</p>
      <span class="price">¥{{ goodsItem.price }}</span>
      <span class="collect">{{ goodsItem.cfav }}</span>
    </div>
  </div>
</template>
<script>
export default {
  name: "GoodsListItem",
  props: {
    goodsItem: {
      type: Object,
      default() {
        {
          return {};
        }
      },
    },
  },

  methods: {
    imageLoad() {
      // 提交一个事件
      // this.$bus.$emit("itemImageLoad");
    },
    itemClick(){
      let iid = this.goodsItem.iid
      this.$router.push(`/detail/${iid}`)
    }
  },
  computed:{
    getImg(){
      return this.goodsItem.img || this.goodsItem.image || this.goodsItem.show.img;
    }
  }
};
</script>
<style scoped>
.goods-item {
  padding-bottom: 10px;
  position: relative;
  width: 48%;
}

.goods-item img {
  width: 100%;
  border-radius: 5px;
}
.goods-info {
  font-size: 12px;
  overflow: hidden;
  text-align: center;
  bottom: 5px;
  text-align: center;
}
.goods-info p {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  margin-bottom: 3px;
}
.goods-info .price {
  color: var(--color-high-text);
  margin-right: 20px;
}
.goods-info .collect {
  position: relative;
}
.goods-info .collect::before {
  content: "";
  position: absolute;
  left: -15px;
  top: 0;
  width: 14px;
  height: 14px;
  background: url("~assets/img/common/collect.svg") 0 0/14px 14px;
}
</style>
