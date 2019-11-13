<template>
  <main class="container">
    <div class="columns">
      <div class="column field">
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
      <!-- <div class="column field">
          <label class="label">Enter your iframe URL:</label>
          <div class="control">
            <input
              class="input"
              type="text"
              placeholder="iframe URL"
              v-model="url"
            >
          </div>
      </div> -->
      <div class="column field">
          <label class="label">Enter iframe container width:</label>
          <div class="control">
            <input
              class="input"
              type="text"
              placeholder="iframe width"
              v-model="width"
            >
          </div>
      </div>
    </div>
    <div :width="width">
      <!-- <script :id="url.match(/(SA-)\w+/g)" :src="url"></script> -->
      <script id="SA-NA1PVPYNKCAJZ" src="https://sunrise-go-feature-sn-506-essay-popup-advxqrwbca-uc.a.run.app/SA-NA1PVPYNKCAJZ/frm.js"></script>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      url: 'https://sunrise-go-feature-sn-506-essay-popup-advxqrwbca-uc.a.run.app/SA-NA1PVPYNKCAJZ/frm',
      bg: null,
      width: '800px'
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
}
.iframe-container {
  margin: auto;
}
</style>
