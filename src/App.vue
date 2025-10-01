<script setup lang="ts">
import { onMounted } from 'vue';

onMounted(() => {
  const audio = new Audio('/assets/spooky.mp3');
  audio.loop = true;
  audio.volume = 0.5;

  // Play on first click
  const playAudio = () => {
    audio.play();
    window.removeEventListener('click', playAudio);
  };

  window.addEventListener('click', playAudio);
});
</script>

<template>
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
      <time>🕕 18:00 – 21:00</time><br />
      <address>🏚️ Haunted House – Kosti Palama 47, Ap 23</address>
      <p>🧛 Your Host: CALLIOPE KALENDA</p>
      <audio src="/assets/spooky.mp3" muted autoplay loop></audio>
      <video type="video/mp4" class="video" loop playsinline muted autoplay src="/assets/video-bg.mp4"></video>
    </footer>
  </div>

</template>

<style scoped>
.container {
  --gap: 10px;
  width: calc(340px - var(--gap));
  max-width: 600px;
  height: 100%;
  margin-top: 20px;
  margin-inline: auto;
  padding: var(--gap);
  text-align: center;
  color: #e6e6e6;
  border-radius: 12px;
  background-color: rgba(41, 2, 50, 0.47);
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(12px);
  box-shadow: 0 0 20px rgba(200, 0, 255, 0.3),
  0 0 40px rgba(0, 255, 140, 0.2);
  font-family: "Poppins", sans-serif;
  animation: pulse-shadow 4s infinite alternate ease-in-out;
  overflow: hidden;
}

.video {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 1000px;
  height: auto;
  mix-blend-mode: color-dodge;
  border-radius: 12px;
}

/* Title */
.header h1 {
  font-family: "Nosifer", cursive;
  font-size: 1.6rem; /* readable on small screens */
  color: #ff6600;
  animation: flicker 2s infinite alternate;
  margin-bottom: 1rem;
  line-height: 1.2;
}

/* Subtitle */
.main h2 {
  font-family: "Nosifer", cursive;
  font-size: 1.3rem;
  color: #9d4edd;
  margin-bottom: 0.8rem;
  line-height: 1.3;
}

/* Body text */
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

@keyframes pulse-shadow {
  0% {
    box-shadow: 0 0 15px rgba(200, 0, 255, 0.3),
    0 0 30px rgba(0, 255, 140, 0.2),
    0 0 20px rgba(255, 102, 0, 0.2);
  }
  50% {
    box-shadow: 0 0 40px rgba(200, 0, 255, 0.7),
    0 0 60px rgba(0, 255, 140, 0.5),
    0 0 35px rgba(255, 102, 0, 0.6);
  }
  100% {
    box-shadow: 0 0 15px rgba(200, 0, 255, 0.3),
    0 0 30px rgba(0, 255, 140, 0.2),
    0 0 20px rgba(255, 102, 0, 0.2);
  }
}

/* Flicker Animation */
@keyframes flicker {
  0%, 18%, 22%, 25%, 53%, 57%, 100% {
    opacity: 1;
  }
  20%, 24%, 55% {
    opacity: 0.5;
  }
}

@media (min-width: 600px) {
  .container {
    padding: calc(var(--gap) * 2);
    border-radius: 15px;
    box-shadow: 0 0 25px rgba(200, 0, 255, 0.4),
    0 0 50px rgba(0, 255, 140, 0.3);
  }

  .header h1 {
    font-size: 1.8rem;
  }

  .main h2 {
    font-size: 1.4rem;
  }

  .main p {
    font-size: 1rem;
    line-height: 1.7;
  }

  footer {
    font-size: .8rem;
  }
}
</style>
