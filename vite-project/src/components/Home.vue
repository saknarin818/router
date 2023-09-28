<!-- Home.vue -->
<template>
  <div class="container text-center">
    <div class="row">
      <div
        class="col mt-5"
        v-for="(restaurant, index) in travelList"
        :key="index"
      >
        <div class="card" style="width: 18rem">
          <img
            :src="restaurant.imagesP"
            class="card-img-top"
            :width="sizeW"
            :height="sizeH"
          />
          <div class="card-body">
            <h2>ร้านที่ : {{ index+1 }}</h2>
            <h5 class="card-title">ชื่อร้าน : {{ restaurant.name }}</h5>
            <p class="card-text">ราคาเริ่ม : {{ restaurant.price }}</p>
            <button
              class="btn btn-danger"
              data-bs-toggle="modal"
              data-bs-target="#staticBackdrop"
              @click="goToOtherComponent(restaurant.name, restaurant.imagesP,index)"
            >
              จองโต๊ะ
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'; // import ref

export default {
  methods: {
    goToOtherComponent(name, imagesP,index) {
      // ส่งค่าไปยังคอมโพเนนต์ OtherComponent.vue ผ่านคิวรี่พารามิเตอร์
      this.$router.push({
        name: 'other',
        query: {
          index:index,
          restaurantName: name,
          restaurantImagesP: imagesP,
        },
      });
    },
  },
  setup() {
    const travelList = ref([
      
        {
    name: "TAMMA CAFE",
    price: 1500,
    imagesP:
      "https://scontent.fcnx2-1.fna.fbcdn.net/v/t39.30808-6/361305041_779199773993037_7111305937619716444_n.jpg?_nc_cat=110&ccb=1-7&_nc_sid=a2f6c7&_nc_eui2=AeFxvmteBvy2K79UsDn0RYOZKhovrXyAa8YqGi-tfIBrxpKuFLPrFlvZOGn0EPhZHElf6G2dL5UlEl78fU6V5jXx&_nc_ohc=1UXKSpBNxqsAX_w_S-9&_nc_ht=scontent.fcnx2-1.fna&oh=00_AfC21mZ-kEclwyx0wYfXElAuQzOJJFmb07amlZ6mSIz0mg&oe=651AAFC7"  ,
  },
  {
    name: "ไป-ยานใหญ่",
    price: 1200,
    imagesP:
      "https://scontent.fcnx2-1.fna.fbcdn.net/v/t39.30808-6/326435697_501993212005268_2267045348590722770_n.jpg?_nc_cat=103&ccb=1-7&_nc_sid=a2f6c7&_nc_eui2=AeH0Q4qXNrxJVT54T0cFNC1qxTbvRg4F5HPFNu9GDgXkc81nD3XBuj1ViRYkv6a4ko_BkUgAVzvK9WVhgVuzBefR&_nc_ohc=lCdv4TOlL54AX-ZXGVa&_nc_ht=scontent.fcnx2-1.fna&oh=00_AfDjJc42rs8ot3UkFEGq7QyLb6Aj7yG8minoEJGuYF0aRA&oe=651A6E0F",
  },
  {
    name: "ตะวันแดง",
    price: 1500,
    imagesP:
      "https://scontent.fcnx2-1.fna.fbcdn.net/v/t39.30808-1/357020255_652721053558857_528736678354773129_n.jpg?stp=dst-jpg_p320x320&_nc_cat=105&ccb=1-7&_nc_sid=754033&_nc_eui2=AeFEA72Z2_JUgxLfwAkTB7-B39Zl0-plB1rf1mXT6mUHWshg6om9d-XCUPRwSdAt6zJ6HTJk7MlFcIA2ri34EPSY&_nc_ohc=h0N_M60E0moAX9m3bDt&_nc_ht=scontent.fcnx2-1.fna&oh=00_AfCnuzN9SYzO8235TxnZ7kfhH2gsa2NoA4vTPaGs-lFZCQ&oe=651B5FF5",
  },
  {
    name: "Overnight Bar",
    price: 1000,
    imagesP:
      "https://scontent.fcnx2-1.fna.fbcdn.net/v/t39.30808-1/314943429_107842845474701_641691726405226769_n.jpg?stp=cp6_dst-jpg_p240x240&_nc_cat=107&ccb=1-7&_nc_sid=754033&_nc_eui2=AeFKVdM1ERBKuuApslbJ4L81EYxzLzXtdwsRjHMvNe13C0C0TYGRLuRJi0m3-9z_F4e6c_nxYCUeAg3p_xXb0Jsn&_nc_ohc=fnRRZl4z1tYAX-aoE36&_nc_ht=scontent.fcnx2-1.fna&oh=00_AfCnhcnV0HaOwoshv26Myo18mzumRId7qhj9C5rNFgXgLg&oe=651A6A93",
  },

    ]);

    const sizeW = 350;
    const sizeH = 250;

    return { // return ตัวแปรออกมาจาก setup
      travelList,
      sizeW,
      sizeH,
    };
  },
};
</script>
