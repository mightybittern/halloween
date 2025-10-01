<script setup lang="ts">
import { onMounted } from 'vue';

onMounted(() => {
  const audio = new Audio('/halloween/assets/spooky.mp3');
  audio.loop = true;
  audio.volume = 0.5;

  const playAudio = () => {
    audio.play().catch(err => console.log('Audio blocked:', err));
    window.removeEventListener('click', playAudio);
  };

  window.addEventListener('click', playAudio);
});
</script>

<template>
  <div class="wrapper">
    <!-- Optional background video -->
    <video class="video" autoplay loop muted playsinline src="/assets/video-bg.mp4"></video>

    <!-- Main content container -->
    <div class="container">
      <header class="header">
        <h1>Spooktacular INVITATION</h1>
      </header>

      <main class="main">
        <h2>HALLOWEEN PARTY</h2>
        <p>
          Enter if you dare... <br />
          You are <span class="">creepily summoned</span> to a night of
          frights, laughs, and glowing jack-o'-lantern grins.
        </p>
        <p>
          Costumes are mandatory—don’t let the pumpkin monster catch you without one! 😈
        </p>
      </main>

      <footer>
        <time>🕕 Friday, October 31 @ 18:00 – 21:00</time><br />
        <a href="https://maps.app.goo.gl/Lnam2NSZPBjKixaD8" target="_blank" rel="noopener noreferrer">
          🏚️ Haunted House</a>
        <p>🧛 Your Host: CALLIOPE KALENDA</p>
      </footer>
    </div>
  </div>
</template>

<style scoped>
/* Reset & remove scroll */

/* Fullscreen wrapper */
.wrapper {
  position: relative;
  width: 100%;
  height: 100dvh; /* dynamic viewport height for mobile rotation */
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  background: image-set(
    url("/assets/bg-big.webp") type("image/webp"),
    url("/assets/bg-big.jpg") type("image/jpeg")
  );
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

/* Background video */
.video {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  mix-blend-mode: color-dodge;
  pointer-events: none;
  z-index: 0;
}

/* Content container */
.container {
  position: relative;
  z-index: 1;
  width: 80%;
  max-width: 600px;
  max-height: 90%;
  padding: 1.5rem;
  text-align: center;
  color: #e6e6e6;
  background-color: rgba(41, 2, 50, 0.47);
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(12px);
  border-radius: 20px;
  box-shadow: 0 0 20px rgba(200,0,255,0.3), 0 0 40px rgba(0,255,140,0.2);
  animation: pulse-shadow 4s infinite alternate ease-in-out;
  overflow-y: auto;
  scrollbar-width: none;
}

.container::-webkit-scrollbar {
  display: none; /* Chrome, Safari, Edge */
}

/* Header */
.header h1 {
  font-family: "Nosifer", cursive;
  font-size: 1.6rem;
  color: #ff6600;
  animation: flicker 2s infinite alternate;
  margin-bottom: 1rem;
  line-height: 1.2;
}

/* Main */
.main h2 {
  font-family: "Nosifer", cursive;
  font-size: 1.3rem;
  color: #9d4edd;
  margin-bottom: 0.8rem;
  line-height: 1.3;
}
.main p {
  font-size: 1.1rem;
  line-height: 1.5;
  text-transform: uppercase;
  font-weight: 900;
  color: #00ff88;
}
.highlight {
  color: #00ff88;
  text-shadow: 0 0 4px #00ff88, 0 0 8px #00ff55;
  font-weight: 600;
}

/* Footer */
footer {
  margin-top: 1.5rem;
  font-size: 0.85rem;
  color: #b3b3b3;
  text-shadow: 0 0 4px #6600ff;
  text-align: left;
}

/* Animations */
@keyframes pulse-shadow {
  0% { box-shadow: 0 0 15px rgba(200,0,255,0.3), 0 0 30px rgba(0,255,140,0.2), 0 0 20px rgba(255,102,0,0.2); }
  50% { box-shadow: 0 0 40px rgba(200,0,255,0.7), 0 0 60px rgba(0,255,140,0.5), 0 0 35px rgba(255,102,0,0.6); }
  100% { box-shadow: 0 0 15px rgba(200,0,255,0.3), 0 0 30px rgba(0,255,140,0.2), 0 0 20px rgba(255,102,0,0.2); }
}
@keyframes flicker {
  0%,18%,22%,25%,53%,57%,100% { opacity: 1; }
  20%,24%,55% { opacity: 0.5; }
}

/* Media queries */
@media (min-width: 600px) {
  .container {
    width: 80%;
    max-height: 85%;
    box-shadow: 0 0 25px rgba(200,0,255,0.4), 0 0 50px rgba(0,255,140,0.3);
  }
  .header h1 { font-size: 1.8rem; }
  .main h2 { font-size: 1.4rem; }
  .main p { font-size: 1rem; line-height: 1.7; }
  footer { font-size: 0.8rem; }
}
</style>
