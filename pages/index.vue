<template>
  <main class="container">
    <form @submit.prevent="generate" class="columns is-multiline">
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
      <div class="column field">
          <label class="label">Enter your iframe URL:</label>
          <div class="control">
            <input
              ref="url"
              class="input"
              type="text"
              placeholder="iframe URL"
              required
            >
          </div>
      </div>
      <!-- <div class="column field">
          <label class="label">Enter iframe container width:</label>
          <div class="control">
            <input
              class="input"
              type="text"
              placeholder="iframe width"
              v-model="width"
            >
          </div>
      </div> -->
      <div class="column is-12">
        <button class="button is-primary is-rounded" :class="{ 'is-loading': loading }">Generate iframe</button>
      </div>
    </form>
    <div v-if="url" class="iframe-container">
      <script :id="iframeID(url)" :src="url" @load="loading = false" />
      <!-- <script id="SA-NA1PVPYNKCAJZ" src="https://sunrise-go-feature-sn-506-essay-popup-advxqrwbca-uc.a.run.app/SA-NA1PVPYNKCAJZ/frm.js"></script> -->
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      url: null,
      bg: null,
      loading: false
    }
  },
  methods: {
    updateBg() {
      document.documentElement.style.setProperty('--bg-color', this.bg);
    },
    generate() {
      this.url = this.$refs.url.value;
      this.loading = true;
    },
    iframeID(url) {
      url.match(/(SA-)\w+/g);
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
  height: 2000px;
}
.iframe-container > iframe {
  height: 100%;
}
.button {
  display: flex;
  margin: auto;
}
</style>
