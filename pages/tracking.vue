<template>
  <h1>A page to test SPA behaviour for the provider side tracking script</h1>
</template>

<script>
export default {
  name: "tracking",
  head: {
    script: [
      { src: 'https://sapp-go-sn-1752-advertiser-tracking-advxqrwbca-ew.a.run.app/trk.js', defer: true },
      { src: '/tracking.js', body: true },
    ]
  },
}
</script>
