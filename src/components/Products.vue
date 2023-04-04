<template>
  <div class="productcard" v-if="productList.length > 0">
    <h1>List Of Added Products</h1>
    <hr />
    <div class="addedcard">
      <div
        class="itemcard"
        v-for="productItem in productList"
        :key="productItem"
      >
        <img
          class="selectedimage"
          :src="productItem.selectedImage"
          :alt="productItem.title"
        />

        <div class="carddetails">
          <h4 class="cardname">{{ productItem.title }}</h4>

          <small><strong> Count : </strong>{{ productItem.count }}</small>

          <small><strong> Price : </strong>{{ productItem.price }}</small>

          <small><strong> Total : </strong>{{ productItem.totalPrice }}</small>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["productList"],
};
</script>

<style lang="scss">
.productcard {
  margin-top: 50px;
  padding: 50px 50px;
  background-color: #fff;
  border-radius: 20px;
  box-shadow: 0 21px 87px -35px rgba(#5062d3, 0.5);
  .addedcard {
    display: flex;
    flex-wrap: wrap;
    column-gap: 40px;
    row-gap: 40px;

    .itemcard {
      padding: 4px;
      border: 1px solid darken(#e7eafb, 3%);
      border-radius: 8px;
      font-size: 17px;
      background: #e7eafb;
      display: flex;
      color: #111127;
      align-items: center;
      flex-direction: column;
      height: 220px;
      width: 170px;
      transition: 300ms transform;
      row-gap: 6px;
      &:hover {
        background: darken(#e7eafb, 3%);
        transform: scale(1.03);
      }
      .selectedimage {
        border-radius: 8px;
        height: 110px;
        width: 160px;
        object-fit: cover;
      }
      .carddetails {
        display: flex;
        align-items: center;
        flex-direction: column;
        .cardname {
          font-size: 18px;
          font-weight: bold;
          color: #ff6da1;
          margin: 5px 0;
        }
        small {
          font-size: 15px;
          color: #111127;
        }
      }
    }
  }
  h1 {
    margin-bottom: 50px;
    color: #111127;
    font-size: 35px;
    font-weight: bold;
    display: flex;
    justify-content: center;
  }
}
</style>
