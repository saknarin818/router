<!-- OtherComponent.vue -->
<template>
  <div>
    <h1 class="text-center">ร้านที่ {{receivedIndex  }}</h1>
    <p class="text-center">ชื่อร้าน {{ receivedRestaurantName }}</p>
    <img :src="receivedRestaurantImagesP" alt="" srcset="">
<br/>
    <button @click="goToHome">Go to Home</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      receivedRestaurantName: null,
      receivedRestaurantImagesP: null,
      receivedIndex: null,
    };
  },
  created() {
    // ใช้ $route.query เพื่อรับข้อมูลที่ถูกส่งผ่านคิวรี่พารามิเตอร์
    this.receivedRestaurantName = this.$route.query.restaurantName;
    this.receivedRestaurantImagesP = this.$route.query.restaurantImagesP;
    this.receivedIndex = parseInt(this.$route.query.index)+1 ;
  },
  methods: {
    goToHome() {
      // ส่งค่าไปยังคอมโพเนนต์ Home.vue
      this.$router.push({ name: 'home' });
    },
  },
};
</script>
<style>
div {
  text-align: center;
  padding: 20px;
}

h1 {
  font-size: 24px;
}

p {
  font-size: 16px;
  margin-top: 10px;
}

img {
  max-width: 100%;
  height: 300px;
  margin-top: 20px;
}

button {
  margin-top: 20px;
  padding: 10px 20px;
  background-color: #007BFF;
  color: #fff;
  border: none;
  cursor: pointer;
  font-size: 16px;
  border-radius: 4px;
}

button:hover {
  background-color: #0056b3;
}

</style>