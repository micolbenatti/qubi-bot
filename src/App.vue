<template>
  <div>
    <div id="navbar" class="flex items-center justify-between w-full h-20 bg-white/90 backdrop-blur-md p-4 fixed top-0 z-50 text-[var(--primary)] font-bold ">
      <router-link to="/" class="logo"><img src="/logo-bot.png" alt="Logo QUBI" class="logo-img"></router-link>

      <!-- <router-link to="/menu" class="link">Menù</router-link> -->

      <router-link to="/contatti" class="link">Contatti</router-link>
    </div>

    <main class="w-full h-full pt-20 flex items-center justify-center">
      <router-view @apri-chat="chatVisibile = true" />
    </main>

    <Embed v-if="chatVisibile" @chiudi="chatVisibile = false" />

    <footer class="footer">
        <div class="footer-left">
          <h3>Consulta il manuale</h3>
          <a class="manuale-btn" href="/manuale.pdf">CLICCA QUI</a>
        </div>
    </footer>

  </div>
</template>

<script setup>
import { ref } from 'vue'
import Embed from './components/embed.vue'

const chatVisibile = ref(false)
</script>

<style scoped>

#navbar {
  box-shadow: 0 2px 6px rgba(62, 32, 14, 0.2);
}

.logo {
  display: flex;
  justify-content: center;
  align-items: center;
}

.logo-img {
  height: 3rem;
  object-fit: contain;
}

.link {
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
  color: var(--primary);
  transition: background-color 0.2s ease, color 0.2s ease;
}

.link:hover {
  background-color: rgba(62, 32, 14, 0.08);
}

.router-link-active.link,
.router-link-exact-active.link {
  background-color: var(--primary);
  color: #fff;
}

.footer {
  background-color: #fffbf8;
  padding: 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  border-top-left-radius: 60px;
  border-top-right-radius: 60px;
  margin-bottom: 0;
  padding-bottom: 0;
  height: 10rem;
}

.footer-left h3 {
  font-size: 1.3rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.manuale-btn {
  background-color: var(--secondary);
  color: white;
  font-weight: 700;
  border: none;
  border-radius: 10px;
  padding: 0.75rem 2rem;
  font-size: 0.9rem;
  transition: background-color 0.2s ease;
  text-transform: uppercase;
}

.manuale-btn:hover {
  background-color: var(--primary);
}

.footer-img {
  width: 18rem;
  height: auto;
  display: block; 
}

</style>
