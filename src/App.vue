<template>
  <div id="app">
    <h1>Caesar Cipher</h1>

    <div class="tab-menu">
      <p id="encrypt-btn" ref="encryptBtn" @click="selectEncrypt">Encrypt</p>
      <p>//</p>
      <p id="decrypt-btn" ref="decryptBtn" @click="selectDecrypt">Decrypt</p>
    </div>

    <TabEncrypt v-if="tabSelected"/>
    <TabDecrypt v-else/>
  </div>
</template>

<script>
import TabEncrypt from "./components/TabEncrypt.vue";
import TabDecrypt from "./components/TabDecrypt.vue";

export default {
  name: "app",
  components: {
    TabEncrypt,
    TabDecrypt
  },
  data() {
    return {
      tabSelected: true
    };
  },
  methods: {
    selectEncrypt() {
      this.tabSelected = true;
      this.$refs.encryptBtn.style.color = "var(--secondary)";
      this.$refs.decryptBtn.style.color = "var(--primary)";
    },
    selectDecrypt() {
      this.tabSelected = false;
      this.$refs.decryptBtn.style.color = "var(--secondary)";
      this.$refs.encryptBtn.style.color = "var(--primary)";
    }
  }
};
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
}

:root {
  --primary: #2c3e50;
  --secondary: #4f99e4;
  --accent: green;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  color: var(--primary);
  margin: 0;
  padding: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: linear-gradient(45deg, #fff722, #ff26f9);
  box-shadow: inset -20px 0 38px -18px #ff26f9,
    inset -3px -13px 65px -18px yellow;
}

h1 {
  font-size: 2em;
}

p {
  font-size: 1.5em;
  margin: 50px 5px;
}

.tab-menu {
  display: flex;
  justify-content: center;
  align-items: center;
}

#encrypt-btn,
#decrypt-btn {
  cursor: pointer;
}

#encrypt-btn:hover,
#decrypt-btn:hover {
  color: var(--secondary);
}

#encrypt-btn {
  color: var(--secondary);
}

#decrypt-btn {
  color: var(--primary);
}
</style>
