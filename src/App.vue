<template>
  <!-- <h1>Hello</h1>
  <h2 v-if="check">{{ title }}</h2>
    <button @click="$event=>check = !check">Ẩn/Hiện</button>
    <button @click="tangso">Tăng</button>
    <button :disabled = "isDisable" @click="giamso">Giảm</button>
  <b>{{ count }}</b>
  <ul>
    <li :key="i" v-for="(ani , i) in animals">{{ ani }}</li>
  </ul>
  <input type="text" v-model="title">
  <h1>One way binding</h1>
  <h2>{{ title }}</h2>
  <p>
    <a v-bind:href="link">Click to google.com</a>
  </p>
           <h4 v-html="content"></h4>
  <img :src="image" alt="" width="200px">
  <h4>{{ XinChao("Lê Tuấn Đạt") }}</h4>
  <br>
  <h1>Two way databinding</h1>
  <h4>Đây là con:{{ animal.join(', ') }}</h4>
  <input type="text" v-model.lazy="animal">
  <br>
  <select v-model="animal" multiple>
    <option value="mèo">Mèo</option>
    <option value="gà">Gà </option>
    <option value="chó">Chó</option>
  </select>
  <h4>Giới tính:{{ gender }}</h4>
  <input type="radio" v-model="gender" value="Nam">Nam
  <input type="radio" v-model="gender" value="Nữ">Nữ
  <br>
  <form action="" @submit.prevent="formSubmit">
  <p>
    Họ tên <input v-model="dataForm.name">
  </p>
  <p>
      Số điện thoại <input v-model="dataForm.sdt">
  </p>
  <button>submit</button>
  </form>
  <br>
  <h1>Computed</h1>
  <h2>Hi:{{ fullName() }}</h2>
  <h2>{{ fullName1 }}</h2>
  <input v-model="firstName" type="text" name="" id="">
  <input v-model="lastName" type="text" name="" id="">
  <button @click="changeFullName">click</button> -->

  <div class="cart-container">
    <div class="cart" :key="product" v-for="product in products" :style="{ background: product.isCart ? 'red' : '#fff' }"
      @dblclick="onToggleCart($event, product)">
      <img class="img" :src="product.image" alt="">
      <h3>{{ product.name }}</h3>
      <h4>{{ product.price }}</h4>
      <button @click="deleteItem(product)">Delete</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [
        {
          name: "iphone13",
          price: 200,
          isCart: false,
          image: "https://stcv4.hnammobile.com/downloads/f/tong-hop-50-hinh-anh-iphone-15-moi-nhat-tren-thi-truong-hien-nay-01699258796.jpg"
        },
        {
          name: "iphone14",
          price: 150,
          isCart: false,
          image: "https://cdn.xtmobile.vn/vnt_upload/news/04_2022/29/man-hinh-iphone-14-pro-xtmobile.jpg"
        },
        {
          name: "iphone15",
          price: 100,
          isCart: false,
          image: "https://news.khangz.com/wp-content/uploads/2022/09/khung-vien-cua-nhung-phien-ban-iphone-14-duoc-lam-tu-titan-1-750x536.jpg"
        },

      ],




      dataForm: {
        name: "",
        sdt: ""
      },
      firstName: "Lê Tuấn",
      lastName: "Đạt",
      gender: "",
      animal: [],
      title: "Xin chào",
      count: 0,
      check: true,
      link: "https://google.com",
      content: '<strong>hello</strong>',
      image: 'https://www.elle.vn/wp-content/uploads/2017/07/25/hinh-anh-dep-1.jpg',
      fullname: "Lê Tuấn Đạt",
      isDisable: false,
      animals: [
        'Mèo',
        'Chó',
        'Gà'
      ]
    }
  },
  methods: {
    tangso() {
      this.isDisable = this.count < 1 ? true : false;
      this.count++
    },
    giamso() {
      this.isDisable = this.count <= 1 ? true : false;
      this.count--;
    },
    hello: (my_name) => {
      return "Xin chào" + my_name;
    },
    XinChao: (my_name) => {
      return "Xin Chào" + my_name;
    },
    formSubmit() {
      console.log(this.dataForm)
    },
    fullName() {
      console.log("Họ và tên")
      return this.firstName + ' ' + this.lastName
    },
    changeFullName() {
      this.fullName1 = "Haahahah";
    },
    onToggleCart(event, product) {
      product.isCart = !product.isCart
    },
    deleteItem() {
      this.products.splice(this.products, 1);
    }
  },
  computed: {
    fullName1: {
      get() {
        return this.firstName + " " + this.lastName;

      },
      set(value) {
        return this.firstName = value
      }
    },
    productComputed() {
      return this.products.filter((product) => product.price < 200)
    }

  }
}
</script>
<style>
.cart-container {
  display: flex;
  justify-content: start;
  align-items: center;
}

.cart {
  width: 180px;

  background-color: aqua;
  margin-bottom: 20px;
}

.img {
  width: 200px;
  height: auto;
}
</style>