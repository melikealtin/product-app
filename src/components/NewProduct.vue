<template>
  <div class="firstcomponent">
    <div class="addimage">
      <img
        class="image"
        height="120"
        :src="
          product.selectedImage == null
            ? '/src/assets/camera.png'
            : product.selectedImage
        "
      />
      <input
        ref="file"
        type="file"
        style="display: none"
        @change="onChange($event)"
      />
      <button class="selectimage" type="button" @click="$refs.file.click()">
        Select İmage
      </button>
    </div>
    <div class="addproduct">
      <form @submit.prevent="addProduct">
        <div class="writeproduct">
          <div class="select">
            <label>Name of the product:</label>
            <input
              type="text"
              v-model="product.title"
              placeholder="enter your name"
            />
          </div>
          <div class="select">
            <label>Number of products:</label>
            <input
              type="text"
              v-model="product.count"
              placeholder="enter the number"
            />
          </div>
          <div class="select">
            <label>Product price:</label>
            <input
              type="text"
              v-model="product.price"
              placeholder="enter price"
            />
          </div>
        </div>
        <button class="additem" @submit="addProduct">Add</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      product: {
        title: null,
        count: null,
        price: null,
        totalPrice: null,
        selectedImage: null,
      },
    };
  },
  methods: {
    onChange(e) {
      const file = e.target.files[0];
      this.product.selectedImage = URL.createObjectURL(file);
      // console.log(URL.createObjectURL(file));
    },
    addProduct() {
      this.product.totalPrice = this.product.count * this.product.price;
      this.$emit("product", this.product);
      this.product = {
        title: null,
        count: null,
        price: null,
        totalPrice: null,
        selectedImage: null,
      };
    },
  },
};
</script>

<style lang="scss">
.firstcomponent {
  margin-top: 30px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  column-gap: 40px;
  .addimage {
    width: 180px;
    height: 200px;
    display: flex;
    align-items: center;
    flex-direction: column;
    row-gap: 40px;
    .image {
      border-radius: 8px;
      height: 100px;
      width: 150px;
    }
    .selectimage {
      background: #8a9cff;
      height: 30px;
      width: 100px;
      font-size: 13px;
      font-weight: bold;
      border-radius: 8px;
      cursor: pointer;
      color: #fff;
      box-shadow: 0 11px 30px -15px #6778e1;
      transition: 300ms background-color;

      &:hover {
        background: darken(#8a9cff, 10%);
      }
    }
  }
  .addproduct {
    height: 200px;
    width: 300px;
    .writeproduct {
      margin-top: -10px;
      .select {
        display: flex;
        flex-direction: column;
        margin: 3px;
        margin-bottom: 0.5em;
        label {
          color: #111127;
          font-size: 15px;
          margin-bottom: 0.3em;
        }
        input {
          border: 2px solid #e7eafb;
          background: #ffffff;
          border-radius: 4px;
          cursor: pointer;
          padding: 1em 0.5em;
          height: 25px;
          transition: 300ms border-color;

          &:hover {
            border-color: darken(#e7eafb, 3%);
          }
          &:focus {
            border-color: #8a9cff;
          }
        }
      }
    }
    .additem {
      background: #8a9cff;
      height: 30px;
      width: 100px;
      font-size: 13px;
      font-weight: bold;
      border-radius: 8px;
      cursor: pointer;
      color: #fff;
      box-shadow: 0 11px 30px -15px #6778e1;
      transition: 300ms background-color;
      margin-top: 5px;

      &:hover {
        background: darken(#8a9cff, 10%);
      }
    }
  }
}
</style>
