<template>
  <div
    id="app"
    ref="app"
  >
    <h1 @click="selectHowTo">CAESAR CIPHER</h1>

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

    <TabHowTo v-if="tabSelected === 'how-to'" />
    <TabEncrypt v-else-if="tabSelected === 'encrypt'" />
    <TabDecrypt v-else />

    <a
      href="https://github.com/ayruun/caesar-cipher"
      target="_blank"
      id="link-btn"
    >
      <button>Open on GitHub</button>
    </a>
  </div>
</template>

<script>
import TabHowTo from "./components/TabHowTo.vue";
import TabEncrypt from "./components/TabEncrypt.vue";
import TabDecrypt from "./components/TabDecrypt.vue";

export default {
  name: "app",
  components: {
    TabHowTo,
    TabEncrypt,
    TabDecrypt
  },
  data() {
    return {
      tabSelected: "how-to"
    };
  },
  methods: {
    selectHowTo() {
      this.tabSelected = "how-to";
      this.$refs.encryptBtn.style.color = "var(--primary)";
      this.$refs.decryptBtn.style.color = "var(--primary)";
      this.$refs.app.style.background =
        "linear-gradient(45deg, var(--rose), var(--mint))";
      this.$refs.app.style["box-shadow"] =
        "inset -20px 0 38px -18px var(--mint), inset -3px -13px 65px -18px var(--rose)";
    },
    selectEncrypt() {
      this.tabSelected = "encrypt";
      this.$refs.encryptBtn.style.color = "var(--yellow)";
      this.$refs.decryptBtn.style.color = "var(--primary)";
      this.$refs.app.style.background =
        "linear-gradient(45deg, var(--yellow), var(--pink))";
      this.$refs.app.style["box-shadow"] =
        "inset -20px 0 38px -18px var(--pink), inset -3px -13px 65px -18px var(--yellow)";
    },
    selectDecrypt() {
      this.tabSelected = "decrypt";
      this.$refs.decryptBtn.style.color = "var(--green)";
      this.$refs.encryptBtn.style.color = "var(--primary)";
      this.$refs.app.style.background =
        "linear-gradient(45deg, var(--green), var(--purple))";
      this.$refs.app.style["box-shadow"] =
        "inset -20px 0 38px -18px var(--purple), inset -3px -13px 65px -18px var(--green)";
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Cinzel&display=swap");

html,
body {
  margin: 0;
  padding: 0;
}

:root {
  --primary: #2c3e50;
  --yellow: #f1eb22;
  --pink: #eb34e5;
  --green: #35e08be3;
  --purple: #5f2fcf;
  --mint: rgb(170, 255, 213);
  --rose: rgb(255, 154, 201);
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
  background: linear-gradient(45deg, var(--rose), var(--mint));
  box-shadow: inset -20px 0 38px -18px var(--mint),
    inset -3px -13px 65px -18px var(--rose);
}

h1 {
  font-family: "Cinzel", serif;
  font-size: 56px;
}

h1:hover {
  cursor: pointer;
  color: var(--yellow);
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
  color: var(--primary);
}

#decrypt-btn {
  color: var(--primary);
}

.how-to,
.tab-encrypt,
.tab-decrypt {
  height: 300px;
  width: 50vw;
  background: white;
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

#link-btn {
  margin: 50px;
}

#link-btn button {
  color: white;
  padding: 7px 10px;
  background: var(--primary);
  border-radius: 5px;
  border: none;
  cursor: pointer;
}

#link-btn button:hover {
  background: grey;
}

#link-btn button:focus {
  outline: none;
}

@media (max-width: 500px) {
  h1 {
    font-size: 35px;
  }

  .how-to,
  .tab-encrypt,
  .tab-decrypt {
    width: 70vw;
  }
}
</style>
