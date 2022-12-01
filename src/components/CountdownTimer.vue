<script>
export default {
  name: "CountdownTimer",
  data: () => {
    return {
      displayDays: 0,
      displayHours: 0,
      displayMinutes: 0,
      displaySeconds: 0,
    };
  },
  computed: {
    _seconds: () => 1000,
    _minutes() {
      return this._seconds * 60;
    },
    _hours() {
      return this._minutes * 60;
    },
    _days() {
      return this._hours * 24;
    },
  },
  mounted() {
    this.showremaining();
  },
  methods: {
    formatNum(num) {
      return num < 10 ? "0" + num : num;
    },
    showremaining() {
      const timer = setInterval(() => {
        const now = new Date();
        const end = new Date(2022, 11, 17);
        const distance = end.getTime() - now.getTime();

        if (distance < 0) {
          clearInterval(timer);
          return;
        }

        const days = Math.floor(distance / this._days);
        const hours = Math.floor((distance % this._days) / this._hours);
        const minutes = Math.floor((distance % this._hours) / this._minutes);
        const seconds = Math.floor((distance % this._minutes) / this._seconds);

        this.displayMinutes = this.formatNum(minutes);
        this.displaySeconds = this.formatNum(seconds);
        this.displayDays = this.formatNum(days);
        this.displayHours = this.formatNum(hours);
      }, 1000);
    },
  },
};
</script>
<template>
  <figure class="days">
    <div class="counter">
      <div class="half-bloc">
        <span class="half-circle-left"></span>
        <span class="half-circle-right"></span>
      </div>
      <div class="counter-value days">{{ displayDays }}</div>
    </div>
    <h2 class="counter-title">DAYS</h2>
  </figure>

  <figure class="hours">
    <div class="counter">
      <div class="half-bloc">
        <span class="half-circle-left"></span>
        <span class="half-circle-right"></span>
      </div>
      <div class="counter-value hours">{{ displayHours }}</div>
    </div>
    <h2 class="counter-title">HOURS</h2>
  </figure>

  <figure class="minutes">
    <div class="counter">
      <div class="half-bloc">
        <span class="half-circle-left"></span>
        <span class="half-circle-right"></span>
      </div>
      <div class="counter-value minutes">{{ displayMinutes }}</div>
    </div>
    <h2 class="counter-title">MINUTES</h2>
  </figure>

  <figure class="seconds">
    <div class="counter">
      <div class="half-bloc">
        <span class="half-circle-left"></span>
        <span class="half-circle-right"></span>
      </div>
      <div class="counter-value seconds">{{ displaySeconds }}</div>
    </div>
    <h2 class="counter-title">SECONDS</h2>
  </figure>
</template>

<style scoped>
figure {
  width: 20%;
  height: 50%;
  padding: 1rem;
  display: flex;
  align-items: center;
  justify-content: space-around;
  flex-direction: column;
}
.counter {
  position: relative;
  width: 100%;
  height: 70%;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: var(--clr-ntrl-blue);
  border-radius: 0.75rem;
  box-shadow: 0px 10px 0px 0px var(--clr-ntrl-deep-dark-blue);
  -webkit-box-shadow: 0px 10px 0px 0px var(--clr-ntrl-deep-dark-blue);
  -moz-box-shadow: 0px 10px 0px 0px var(--clr-ntrl-deep-dark-blue);
}
.half-bloc {
  z-index: 10;
  position: absolute;
  top: 0;
  width: 100%;
  height: 50%;
  background-color: var(--clr-ntrl-dark-blue);
  opacity: 30%;
  border-bottom: 1.5px solid black;
}
.half-circle-left,
.half-circle-right {
  z-index: 20;
  position: absolute;
  bottom: -0.4rem;
  width: 0.4rem;
  height: 0.8rem;
  background-color: black;
}
.half-circle-left {
  left: 0;
  border-radius: 0 0.4rem 0.4rem 0;
}
.half-circle-right {
  right: 0;
  border-radius: 0.4rem 0 0 0.4rem;
}
.counter-value {
  font-size: 5rem;
  color: var(--clr-primary-red);
}
.counter-title {
  width: 100%;
  height: 20%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--clr-primary-blue);
  font-size: 1rem;
  letter-spacing: 0.4rem;
}

/* Breakpoint for tablet */
@media (max-width: 768px) {
  figure {
    width: 25%;
  }
  figure .counter-value {
    font-size: 3rem;
  }
  .counter-title {
    font-size: 0.7rem;
    letter-spacing: 0.3rem;
  }
}

/* Breakpoint for mobile */
@media (max-width: 375px) {
  figure {
    height: 40%;
  }
  figure .counter-value {
    font-size: 1.5rem;
  }
  .counter-title {
    font-size: 0.55rem;
  }
}
</style>
