<template>
  <div class="container">
    <div>
      <logo />
      <h1 class="title">test</h1>
      <h2 class="subtitle">{{ip}}</h2>
      <div class="links">
        <button @click="test">Test</button>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from "~/components/Logo.vue";

export default {
  data() {
    return {
      ip: ""
    };
  },
  components: {
    Logo
  },
  methods: {
    async test() {
      const ip = await this.$axios.$get("http://icanhazip.com");
      this.ip = ip;
    }
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
