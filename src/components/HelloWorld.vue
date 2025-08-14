<template>
  <div>
    <header class="header">
      <h1 class="logo-placeholder">Owusu Buaheng</h1>
      <svg
        class="menu-btn"
        id="menu-btn"
        @click="isOpen = !isOpen"
        xmlns="http://www.w3.org/2000/svg"
        height="24px"
        viewBox="0 -960 960 960"
        width="24px"
        fill="#102649"
      >
        <path d="M120-240v-80h720v80H120Zm0-200v-80h720v80H120Zm0-200v-80h720v80H120Z" />
      </svg>

      <nav class="nav-bars" id="nav-bars">
        <a href="#about" class="nav-bar">About</a>
        <a href="#schedule" class="nav-bar">Countdown</a>
        <a href="#speakers" class="nav-bar">Panelists</a>
      </nav>
    </header>

    <nav :class="isOpen ? 'nav-menu' : 'hidden'" id="nav-menu">
      <a href="#about" class="nav-link">About</a>
      <a href="#schedule" class="nav-link">Countdown</a>
      <a href="#speakers" class="nav-link">Panelists</a>
    </nav>

    <main>
      <div class="main-body">
        <h1><b>Welcome to Project Defence 2025</b></h1>
        <p>A Comparative Analysis of Front-End Optimisation Methods for Reducing Web Page Load Time</p>
        <img
          src="/src/assets/images/Edinburgh_logo.png"
          alt="University of Edinburgh logo"
          class="edin-logo"
        />
      </div>

      <div class="shadow-cont" id="about">
        <h2><b>About the Defense</b></h2>
        <p>
          Project Defense 2025 presents a benchmarking study comparing HTML and JavaScript frameworks, measuring performance metrics and optimisation techniques under controlled conditions.
        </p>
      </div>

      <div class="shadow-cont" id="schedule">
        <h2>Countdown to Defense</h2>
        <div class="countdown-cont">
          <img
            src="/src/assets/images/countdown-clock.jpg"
            alt="clock countdown"
            class="countdown-img"
          />
          <div class="timer-cont">
            <h3 class="countdown-text">Time Details</h3>
            <p class="def-date">Defence Date: 28-08-2025</p>
            <div class="countdown-timer" id="countdown-timer">
              <p>Current Date: <span id="date">{{ todayDate }}</span></p>
              <p>Current Time: <span id="time">{{ currentTime }}</span></p>
            </div>
          </div>
        </div>
      </div>

      <div class="shadow-cont" id="speakers">
        <h2><b>Meet the Panelists</b></h2>
        <h3>Supervisor for MSc Dissertation</h3>
        <ul>
          <li class="info">Andreas Steyven</li>
          <li class="info">Email: A.Steyven&#64;napier.ac.uk</li>
        </ul>
        <h3>Internal Examiner</h3>
        <ul>
          <li class="info">Simon Wells</li>
          <li class="info">Email: S.Wells&#64;napier.ac.uk</li>
        </ul>
      </div>
    </main>

    <footer>
      Owusu Buaheng | Copyright &copy; 2025
    </footer>
  </div>
</template>

<script setup>
  import { ref, onMounted, onUnmounted } from 'vue'

  const isOpen = ref(false)
  const todayDate = ref('')
  const currentTime = ref('')

  function updateDateTime() {
    const now = new Date()
    todayDate.value = now.toDateString()
    const hh = now.getHours().toString().padStart(2, '0')
    const mm = now.getMinutes().toString().padStart(2, '0')
    const ss = now.getSeconds().toString().padStart(2, '0')
    currentTime.value = `${hh}:${mm}:${ss}`
  }

  let intervalId

  onMounted(() => {
    updateDateTime()
    intervalId = setInterval(updateDateTime, 1000)
  })

  onUnmounted(() => {
    clearInterval(intervalId)
  })
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Arizonia&family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&family=Lato:ital,wght@0,100;0,300;0,400;0,700;0,900;1,100;1,300;1,400;1,700;1,900&family=Oswald:wght@200..700&family=Roboto:ital,wght@0,100..900;1,100..900&display=swap');

* {
  box-sizing: border-box;
  font-family: "Inter", cursive;
}

body {
  margin: 0;
  padding: 0;
}

.logo-placeholder {
font-size: 25px;
font-family: "Arizonia", cursive;
font-weight: 700;
}

.main-body {
  text-align: center;
  background: #2294f2;
  padding: 60px 20px;
  height: 90vh;
  color: white;
  font-size: 18px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.main-body {
  background-position-x: center;
  background-origin: content-box;
  position: relative;
  background-repeat: no-repeat;
  width: 100%;
  height: 420px;
  background: linear-gradient(#8ea1af, #5592c4),
  url('../assets/images/edinburgh-bg.jpg');
  background-size: cover;
  background-blend-mode: multiply;
}

h2 {
  color: #2294f2;
}

.nav-menu {
  display: flex;
  flex-direction: column;
  justify-content: center;
  background: #494848;
  padding: 5px;
  text-align: center;
}

a.nav-link {
  text-decoration: none;
  color: white;
  padding: 8px 16px;
  width: 180px;
  margin: auto;
  font-weight: 600;
}

a:hover {
  background-color: #2294f2;
  border-radius: 5px;
}

@media screen and (min-width: 768px) {
  .nav-menu {
    display: none;
  }
}

.shadow-cont {
  border: 1px solid #fff;
  border-radius: 10px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  padding: 20px;
  margin: 30px 50px;
  background-color: #eee;
}

#about {
  margin-top: 50px;
}

.header {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  padding: 0 30px;
  background-color: #2294f2;
  color: white;
  background-image: linear-gradient(270deg, #1471bd, #3e9fee, #72b2e6);
}

.hidden {
  display: none;
}

.nav-bars {
  display: none;
}

@media screen and (min-width: 768px) {
  .nav-bars {
    display: grid;
    grid-template-columns: auto auto auto;
    column-gap: 30px;
  }
}

a.nav-bar {
  text-decoration: none;
  color: white;
  padding: 7px 12px;
  font-weight: 600;
}

a.nav-bar:hover {
  background-color: #60aff0;
}

.menu-btn {
  cursor: pointer;
}

@media screen and (min-width: 768px) {
  .menu-btn {
    display: none;
  }
}

.main-body {
  position: relative;
}

.edin-logo {
  position: absolute;
  top: 20px;
  right: 20px;
  width: 130px;
  height: 130px;
  background-color: white;
  padding: 7px;
  border-radius: 100%;
}

.countdown-img {
  height: 320px;
  border: 1px solid #ccc;
  padding: 12px;
  border-radius: 10px;
}

.countdown-cont {
  display: grid;
  grid-template-columns: 1fr 2fr;
  column-gap: 30px;
}

@media screen and (max-width: 768px) {
  .countdown-img {
    width: 100%;
  }
  .countdown-cont {
    grid-template-columns: 1fr;
    row-gap: 30px;
    column-gap: 0;
  }
}

.timer-cont {
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 12px;
  width: 100%;
}

.countdown-text {
  font-size:22px;
  color: #2294f2;
  text-align: center;
}

.def-date {
  margin: 0 0 0 30px;
  font-size: 20px;
  font-weight: 700;
  color: rgb(0, 0, 0, 0.7);
}

.countdown-timer {
  font-weight: 700;
  font-size: 20px;
  background-color: #363333;
  color: white;
  margin: 30px;
  padding: 5px 30px;
  border-radius: 10px;
}

footer {
  padding: 25px 10px;
  text-align: center;
  background-color: #494848;
  color: white;
}

.info {
  opacity: 0.7;
  font-weight: 600;
}

</style>

