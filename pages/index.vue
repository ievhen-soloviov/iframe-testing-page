<template>
  <main class="container">
    <section class="content">
      <div class="has-text-centered mb-1">
        <a href="/tracking" class="button is-primary is-narrow">Tracking Page</a>
      </div>

      <div class="has-text-centered mb-1">
        <a href="/verify" class="button is-primary is-narrow">Verify Goal</a>
      </div>

      <div class="has-text-centered mb-1">
        <a href="/visit" class="button is-primary is-narrow">Visit</a>
      </div>

      <img src="https://upload.wikimedia.org/wikipedia/commons/1/10/Mont_Saint_Michel_bordercropped.jpg" alt="Normandy">
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore
        magna aliqua. Vitae congue eu consequat ac. Enim praesent elementum facilisis leo vel fringilla est. Posuere
        lorem ipsum dolor sit. Euismod in pellentesque massa placerat duis ultricies lacus sed. Elementum eu facilisis
        sed odio morbi quis commodo odio aenean. Netus et malesuada fames ac turpis egestas integer eget aliquet. Ipsum
        dolor sit amet consectetur. Rhoncus urna neque viverra justo nec ultrices dui. Elit sed vulputate mi sit amet
        mauris commodo quis imperdiet. Egestas sed sed risus pretium quam vulputate dignissim suspendisse in.
        Ullamcorper a lacus vestibulum sed arcu.

        Nulla facilisi cras fermentum odio eu feugiat pretium. Tortor id aliquet lectus proin nibh nisl condimentum id
        venenatis. Pellentesque habitant morbi tristique senectus et netus. At augue eget arcu dictum varius duis at
        consectetur lorem. Eget aliquet nibh praesent tristique. Turpis egestas pretium aenean pharetra magna ac.
        Elementum nisi quis eleifend quam adipiscing vitae proin. Nulla porttitor massa id neque aliquam vestibulum
        morbi. Pharetra vel turpis nunc eget lorem. Gravida arcu ac tortor dignissim convallis aenean. Sed odio morbi
        quis commodo odio aenean. Pulvinar sapien et ligula ullamcorper malesuada proin. Tellus orci ac auctor augue
        mauris augue.
      </p>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore
        magna aliqua. Vitae congue eu consequat ac. Enim praesent elementum facilisis leo vel fringilla est. Posuere
        lorem ipsum dolor sit. Euismod in pellentesque massa placerat duis ultricies lacus sed. Elementum eu facilisis
        sed odio morbi quis commodo odio aenean. Netus et malesuada fames ac turpis egestas integer eget aliquet. Ipsum
        dolor sit amet consectetur. Rhoncus urna neque viverra justo nec ultrices dui. Elit sed vulputate mi sit amet
        mauris commodo quis imperdiet. Egestas sed sed risus pretium quam vulputate dignissim suspendisse in.
        Ullamcorper a lacus vestibulum sed arcu.

        Nulla facilisi cras fermentum odio eu feugiat pretium. Tortor id aliquet lectus proin nibh nisl condimentum id
        venenatis. Pellentesque habitant morbi tristique senectus et netus. At augue eget arcu dictum varius duis at
        consectetur lorem. Eget aliquet nibh praesent tristique. Turpis egestas pretium aenean pharetra magna ac.
        Elementum nisi quis eleifend quam adipiscing vitae proin. Nulla porttitor massa id neque aliquam vestibulum
        morbi. Pharetra vel turpis nunc eget lorem. Gravida arcu ac tortor dignissim convallis aenean. Sed odio morbi
        quis commodo odio aenean. Pulvinar sapien et ligula ullamcorper malesuada proin. Tellus orci ac auctor augue
        mauris augue.
      </p>
      <img
        src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/fb/Falaises_Etretat_2012.jpg/640px-Falaises_Etretat_2012.jpg"
        alt="Normandy" class="column">
    </section>

    <form @submit.prevent="generate" class="columns is-multiline">
      <div class="column field">
        <label class="label">Enter background color hex:</label>
        <div class="control">
          <input class="input" type="text" placeholder="color hex" v-model="bg" @input="updateBg">
        </div>
      </div>
      <div class="column field">
        <label class="label">Enter your iframe URL:</label>
        <div class="control">
          <input ref="url" class="input" type="text" placeholder="iframe URL" required>
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
      <div class="column is-12 has-text-centered">
        <button class="button is-primary is-rounded" :class="{ 'is-loading': loading }">Generate iframe</button>
      </div>
    </form>
    <div v-if="url" class="iframe-container">
      <script ref="iframeWrapper" :id="iframeID(url)" :src="url" @load="onLoad" />
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
    };
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
      return url.match(/(SA-)\w+/g);
    },
    onLoad() {
      this.loading = false;
    }
  }
};
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

p:nth-child(1) img {
  float: left;
}

p:nth-child(2) img {
  float: right;
}
</style>
