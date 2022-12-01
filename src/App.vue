<script setup>
import CountdownTimer from "@/components/CountdownTimer.vue";
</script>

<template>
  <header>
    <h1 class="title">WE'RE LAUNCHING SOON</h1>
  </header>
  <main>
    <CountdownTimer />
  </main>
  <footer>
    <div class="img-container">
      <img src="./assets/images/icon-facebook.svg" alt="Facebook logo" />
      <img src="./assets/images/icon-pinterest.svg" alt="Pinterest logo" />
      <img src="./assets/images/icon-instagram.svg" alt="Instagram logo" />
    </div>
  </footer>
</template>

<style scoped>
header {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  flex-wrap: wrap;
}
.title {
  letter-spacing: 0.75rem;
  font-size: 1.5rem;
}
main {
  width: 100%;
  height: 60%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 0 125px 0;
  background-image: url(./assets/images/bg-stars.svg);
  background-repeat: no-repeat;
  background-position: bottom;
  background-size: 100%;
}
footer {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.img-container {
  width: 14rem;
  display: flex;
  align-items: center;
  justify-content: space-around;
}
footer img {
  width: 1.75rem;
}
footer img:hover {
  cursor: pointer;
  filter: invert(54%) sepia(21%) saturate(2169%) hue-rotate(303deg)
    brightness(99%) contrast(99%);
}

/* Breakpoint for tablet */
@media (max-width: 768px) {
  .title {
    font-size: 1rem;
    letter-spacing: 0.5rem;
  }
}

/* Breakpoint for mobile */
@media (max-width: 375px) {
  .title {
    font-size: 0.75rem;
  }
}
</style>
