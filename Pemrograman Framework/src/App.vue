<template>
  <div class="container">
    <button @click="incrementCount" class="primary-btn">Klik Saya</button>
    <p>Jumlah Klik: {{ count }}</p>
    <div :style="{ backgroundColor: boxColor, width: '100px', height: '100px', marginTop: '10px', transition: 'background-color 0.5s ease' }"></div>
    
    <div class="carousel">
      <button @click="prevImage" class="carousel-btn">Previous</button>
      <img :src="images[currentIndex]" alt="Carousel Image">
      <button @click="nextImage" class="carousel-btn">Next</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      colors: ['red', 'blue', 'green', 'yellow', 'purple', 'cyan', 'black', 'orange', 'magenta', 'indigo', 'white', 'gray', 'pink', 'brown', 'maroon', 'beige', 'teal', 'lavender', 'violet', 'turquoise'],
      boxColor: 'red',
      images: [
        'https://s3-ap-northeast-1.amazonaws.com/thegate/2019/06/07/11/48/21/Tokyo-Tower-with-Zojoji-Temple.jpg',
        'https://c2.cloudmatika.com/ivooxs3/wp-content/uploads/2018/12/Mau-Liburan-Akhir-Tahun-Jangan-Hanya-Menara-Eiffel-Kunjungi-Objek-Wisata-ini-Jika-di-Paris-doc.wisata-ivoox.id_.jpg',
        'https://img.okezone.com/content/2015/09/07/406/1209857/mengunjungi-amsterdam-yang-memukau-21umTaBfSA.jpg'
      ],
      currentIndex: 0
    };
  },
  methods: {
    incrementCount() {
      this.count++;
      this.boxColor = this.colors[this.count % this.colors.length];
    },
    prevImage() {
      this.currentIndex = (this.currentIndex - 1 + this.images.length) % this.images.length;
    },
    nextImage() {
      this.currentIndex = (this.currentIndex + 1) % this.images.length;
    }
  }
}
</script>

<style scoped>
/* Container background with an overlay */
.container {
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.8), rgba(0, 168, 255, 0.6)), url('https://via.placeholder.com/1600x900?text=Background+Image');
  background-size: cover;
  background-attachment: fixed;
  background-position: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
  min-height: 100vh;
  text-align: center;
  color: #34495e;
}

/* Buttons styling */
.primary-btn {
  margin: 10px;
  padding: 12px 25px;
  background-color: #00cec9;
  color: white;
  border: none;
  border-radius: 50px;
  cursor: pointer;
  font-size: 1.2rem;
  transition: transform 0.3s ease, background-color 0.3s ease;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
}

.primary-btn:hover {
  background-color: #00b894;
  transform: scale(1.05);
}

.carousel-btn {
  padding: 8px 16px;
  background-color: #dfe6e9;
  border: 2px solid #b2bec3;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease, box-shadow 0.3s ease;
  box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.2);
}

.carousel-btn:hover {
  background-color: #b2bec3;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
}

/* Carousel image styling */
.carousel {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}

img {
  width: 400px;
  height: 300px;
  object-fit: cover;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
  border-radius: 15px;
  transition: transform 0.5s ease;
}

img:hover {
  transform: scale(1.05);
}

/* Typography styling */
p {
  font-size: 1.5rem;
  color: #2d3436;
  margin: 20px 0;
  font-weight: bold;
  letter-spacing: 1.5px;
}

/* Smooth transitions for the color box */
div {
  transition: background-color 0.5s ease;
}
</style>
