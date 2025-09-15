<html lang="zh-Hans"> <head> <title>啊?戈爾舟遊籌措會</title> <meta charset="UTF-8" /> <link rel="icon" href="./icon.ico" type="image/x-icon" /> <script src="https://unpkg.com/vue@3/dist/vue.global.prod.js"></script> <style> body { font-family: Noto Sans TC, sans-serif; margin: 0; padding: 0; overflow: hidden; background-size: cover; background-attachment: fixed; }
.fab_Navbar {
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 9999;
}
.fab_Navbar img { width: 100%; display: block; }

.fab_menu {
  position: fixed;
  top: 1.77%;
  left: 1.77%;
  z-index: 10000;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  visibility: visible;
}
.fab_menu img { width: 1.77%; height: auto; object-fit: cover; }

.container {
  height: 100vh;
  overflow-y: scroll;
  scroll-snap-type: y mandatory;
  scroll-behavior: smooth;
  scrollbar-color: transparent;
}
.container div {
  height: 100vh;
  scroll-snap-align: start;
  scroll-snap-stop: always;
}

.Main_KV { position: relative; z-index: 1; }

.carousel {
  position: relative;
  top: 40%;
  left: 50%;
  transform: translate(-50%, 0);
  width: 100%;
  overflow: hidden;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
  z-index: 2;
  height: 50%;
  width: 50%;
  margin: center;
}

.carousel-container {
  width: 100%;
  height: auto;
  display: flex;
  transition: transform 0.5s ease-in-out;
}

.carousel-slide {
  min-width: 100%;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: transparent;
}

.carousel-slide img {
  align-self: start;
  width: 100%;
}

.carousel-button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(128, 128, 128, 0.5);
  color: white;
  padding: 16px;
  border: none;
  cursor: pointer;
  font-size: 18px;
}

.prev { left: 0%; }
.next { right: 0%; }

.carousel-button:hover {
  background: rgba(0, 0, 0, 0.8);
}
</style> </head> <body style="background-image: url('https://aegirorganizingcommittee-pntdk.wordpress.com/wp-content/uploads/2025/09/index_background.png');"> <div id="app"> <div class="fab_Navbar"> <img src="https://aegirorganizingcommittee-pntdk.wordpress.com/wp-content/uploads/2025/09/index_head.png" draggable="false" /> </div>
<div class="fab_menu">
  <img
    src="https://aegirorganizingcommittee-pntdk.wordpress.com/wp-content/uploads/2025/09/index_icon_menu.png"
    draggable="false"
  />
</div>

<div class="container">
  <div class="Main_KV">
    <img
      src="https://aegirorganizingcommittee-pntdk.wordpress.com/wp-content/uploads/2025/09/index_kv.png"
      style="width: 100%;"
      draggable="false"
    />
  </div>

  <div class="Main_KV">
    <div class="carousel">
      <div
        class="carousel-container"
        :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
      >
        <div class="carousel-slide" v-for="(slide, i) in slides" :key="i">
          <img :src="slide" :alt="`Slide ${i+1}`" draggable="false" />
        </div>
      </div>

      <button class="carousel-button prev" @click="prevSlide">&#10094;</button>
      <button class="carousel-button next" @click="nextSlide">&#10095;</button>
    </div>
  </div>
</div>
</div> <script> const { createApp, ref, onMounted, onUnmounted } = Vue; createApp({ setup() { const slides = ref([ 'https://aegirorganizingcommittee-pntdk.wordpress.com/wp-content/uploads/2025/09/e7b582e5a78be68993e6b395e694bbe795a5.png', 'https://aegirorganizingcommittee-pntdk.wordpress.com/wp-content/uploads/2025/09/e7b582e5a78be6a99fe588b6e8a7a3e69e90.png', 'https://aegirorganizingcommittee-pntdk.wordpress.com/wp-content/uploads/2025/09/e8999be784a1e4b98be581b6e694bbe795a5.png' ]); const currentIndex = ref(0); let timer = null; const updateCarousel = () => { // Vue reactivity updates style binding automatically }; const nextSlide = () => { currentIndex.value = (currentIndex.value + 1) % slides.value.length; updateCarousel(); }; const prevSlide = () => { currentIndex.value = (currentIndex.value - 1 + slides.value.length) % slides.value.length; updateCarousel(); }; const startAuto = () => { stopAuto(); timer = setInterval(nextSlide, 5000); }; const stopAuto = () => { if (timer) { clearInterval(timer); timer = null; } }; onMounted(() => { startAuto(); }); onUnmounted(() => { stopAuto(); }); return { slides, currentIndex, nextSlide, prevSlide }; } }).mount('#app'); </script> </body> </html>
