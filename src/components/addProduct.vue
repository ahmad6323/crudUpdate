<script>
export default {
  name: "addProduct",
  data() {
    return {
      imageURL: null,
      id: "",
      productName: "",
      quantity: "",
      price: "",
      products: [
        {
          id: 1,
          productName: "shirt",
          quantity: 1,
          price: 1,
          imageURL: "./image.png",
          imageURL: "/src/components/image.png",
        },
        {
          id: 2,
          productName: "pants",
          quantity: 3,
          price: 222,
          imageURL: "/src/components/image.png",
        },
      ],
    };
  },
  methods: {
    onFileChange(e) {
      console.log(e)
      const files = e.target.files || e.dataTransfer.files;
      if (!files.length) return;
      this.createImage(files[0]);
    },
    createImage(file) {
      const reader = new FileReader();
      reader.onload = (e) => {
        this.imageURL = e.target.result;
      };
      reader.readAsDataURL(file);
    },
    add() {
      if (this.id.length === 0) return;
      if (this.productName.length === 0) return;
      if (this.quantity.length === 0) return;
      if (this.price.length === 0) return;
      const arr = {
        id: this.id,
        productName: this.productName,
        quantity: this.quantity,
        price: this.price,
        imageURL: this.imageURL,
      };
      this.products.push(arr);

      this.id = "";
      this.productName = "";
      this.quantity = "";
      this.price = "";
      this.imageURL = null
    },
    deleteProduct(index) {
      this.products.splice(index, 1);
    },
    editProduct(id) {
      console.log(id);
      let data = this.products.filter((product) => {
        return product.id === id;
      });
      this.id = data[0].id;
      this.productName = data[0].productName;
      this.quantity = data[0].quantity;
      this.price = data[0].price;
      this.imageURL = data[0].imageURL;
    },
  },
};
</script>
<template>
  <form @submit.prevent="add">
    <div style="margin-left: 30%" class="form-row my-5">
      <div class="form-group col-md-6">
        <label for="inputEmail4">Product ID</label>
        <input
            v-model="id"
            type="number"
            class="form-control mb-4"
            id="1"
            placeholder="Product ID"
        />
      </div>
      <div class="form-group col-md-6">
        <label for="inputEmail4">Product Name</label>
        <input
            v-model="productName"
            type="text"
            class="form-control mb-4"
            id="2"
            placeholder="Product name"
        />
      </div>
      <div class="form-group col-md-6">
        <label for="inputEmail4">Quantity</label>
        <input
            v-model="quantity"
            type="number"
            class="form-control mb-4"
            id="3"
            placeholder="quantity"
        />
      </div>
      <div class="form-group col-md-6">
        <label for="inputEmail4">Price</label>
        <input
            v-model="price"
            type="number"
            class="form-control mb-4"
            id="4"
            placeholder="price"
        />
      </div>

      <div class="form-group col-md-6">
        <label for="formFile" class="form-label"
        >Select image for your product</label
        >
        <input
            class="form-control mb-4"
            type="file"
            id="formFile"
            accept="image/*"
            @change="onFileChange"
        />
      </div>

      <button style="align-items: center" type="submit" class="btn btn-primary">
        ADD
      </button>
    </div>
  </form>
  <table style="width: 800px; margin: 0 auto" class="table table-bordered">
    <thead>
    <tr>
      <th scope="col">Images</th>
      <th scope="col">Product ID</th>
      <th scope="col">Product Name</th>
      <th scope="col">Quantity</th>
      <th scope="col">Price</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="(product, index) in products" :key="index">
      <th>
        <img style="width: 50px" :src="product.imageURL" alt="" />
      </th>
      <th>{{ product.id }}</th>
      <td>{{ product.productName }}</td>
      <td>{{ product.quantity }}</td>
      <td>{{ product.price }}</td>
      <td>
        <button
            type="button"
            class="btn btn-warning"
            @click="editProduct(product.id)"
        >
          Edit
        </button>
      </td>
      <td>
        <button type="button" class="btn btn-danger" @click="deleteProduct">
          Delete
        </button>
      </td>
    </tr>
    </tbody>
  </table>
</template>

<style>

</style>









