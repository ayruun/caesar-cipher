<template>
  <div
    id="app"
    ref="app"
  >
    <h1>Caesar Cipher</h1>

    <div class="tab-menu">
      <p
        id="encrypt-btn"
        ref="encryptBtn"
        @click="selectEncrypt"
      >Encrypt</p>
      <p>//</p>
      <p
        id="decrypt-btn"
        ref="decryptBtn"
        @click="selectDecrypt"
      >Decrypt</p>
    </div>
    
    <TabEncrypt v-if="tabSelected" />
    <TabDecrypt v-else />
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
      this.$refs.encryptBtn.style.color = "var(--accent)";
      this.$refs.decryptBtn.style.color = "var(--primary)";
      this.$refs.app.style.background =
        "linear-gradient(45deg, #fff722, #ff26f9)";
      this.$refs.app.style["box-shadow"] =
        "inset -20px 0 38px -18px #ff26f9, inset -3px -13px 65px -18px #fff722";
    },
    selectDecrypt() {
      this.tabSelected = false;
      this.$refs.decryptBtn.style.color = "#26ff92e3";
      this.$refs.encryptBtn.style.color = "var(--primary)";
      this.$refs.app.style.background =
        "linear-gradient(45deg, #26ff92e3, #6422ff)";
      this.$refs.app.style["box-shadow"] =
        "inset -20px 0 38px -18px #6422ff, inset -3px -13px 65px -18px #26ff92e3";
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
  --accent: #fff722;
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
    inset -3px -13px 65px -18px #fff722;
}

h1 {
  font-size: 50px;
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

#encrypt-btn {
  color: var(--accent);
}

#decrypt-btn {
  color: var(--primary);
}

.tab-encrypt,
.tab-decrypt {
  height: auto;
  width: 50vw;
  background: rgb(255, 255, 255);
  padding: 25px;
  border-radius: 15px;
  box-shadow: 0px 0px 45px -12px rgba(0, 0, 0, 0.75);
}

.headlines {
  font-size: 1.2em;
  margin: 10px 0;
}

input {
  margin-bottom: 25px;
  width: 100%;
  border-radius: 5px;
  padding: 2px;
}

@media (max-width: 500px) {
  h1 {
    font-size: 35px;
  }

  .tab-encrypt,
  .tab-decrypt {
    width: 70vw;
  }
}
</style>
