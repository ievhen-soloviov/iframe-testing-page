<template>
  <main class="container">
    <div class="field">
      <label class="label">Enter background color hex:</label>
        <div class="control">
          <input
            class="input"
            type="text"
            placeholder="color hex"
            v-model="bg"
            @input="updateBg"
          >
        </div>
    </div>
    <div class="field">
        <label class="label">Enter your iframe ID:</label>
        <div class="control">
          <input
            class="input"
            type="text"
            placeholder="iframe ID"
            v-model="id"
          >
        </div>
    </div>
    <p v-if="id">Now showing iframe for ID:<br>{{ id }}</p>
    <template v-if="id">
      <script :id='id' :src='`https://go.sunrising.tech/${id}/frm.js`'></script>
    </template>
  </main>
</template>

<script>
import Logo from '~/components/Logo.vue';

export default {
  components: {
    Logo
  },
  data() {
    return {
      id: null,
      bg: null
    }
  },
  methods: {
    updateBg() {
      document.documentElement.style.setProperty('--bg-color', this.bg);
    }
  }
}
</script>

<style>
:root {
  --bg-color: white;
}
html {
  background-color: var(--bg-color, white);
}
main {
  padding: 1em;
  margin: 1em;
}
</style>
