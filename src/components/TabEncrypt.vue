<template>
  <div class="tab-encrypt">
    <p class="headlines">Encryption Key:</p>
    <div class="generator">
      <input v-model="inputKey" placeholder="Press Generate Button" disabled>
      <button id="key-btn" @click="generateKey">Generate</button>
    </div>

    <p class="headlines">Enter a Message:</p>
    <input v-model="inputMessage" placeholder="Enter your Message to decrypt">

    <p class="headlines">Encrypted:</p>
    <input id="focus-msg" :value="encrypt(inputMessage)">
    <input type="hidden" id="encrypted-msg" :value="encryptedMessage">
    <button id="copy-btn" @click="copyInput">copy</button>
  </div>
</template>

<script>
export default {
  name: "TabEncrypt",
  data() {
    return {
      inputKey: "",
      inputMessage: "",
      encryptedMessage: ""
    };
  },
  methods: {
    encrypt(input) {
      if (!parseInt(this.inputKey)) {
        return "PLEASE GENERATE A KEY!";
      }

      this.encryptedMessage = input
        .split("")
        .map(el => {
          let charCode = el.charCodeAt() + parseInt(this.inputKey);
          return String.fromCharCode(charCode);
        })
        .join("");

      return this.encryptedMessage;
    },
    copyInput() {
      let strToCopy = document.querySelector("#encrypted-msg");
      strToCopy.setAttribute("type", "text");
      strToCopy.select();
      document.execCommand("copy");
      strToCopy.setAttribute("type", "hidden");
      window.getSelection().removeAllRanges();
      let strToFocus = document.querySelector("#focus-msg");
      strToFocus.setAttribute("type", "text");
      setTimeout(function() {strToFocus.select();}, 50);
    },
    generateKey() {
      let min = 100;
      let max = 9999;
      this.inputKey = Math.floor(Math.random() * (max - min) + min);
    }
  }
};
</script>

<style>
#copy-btn {
  width: 100%;
  border-radius: 7px;
  border: none;
  background: var(--yellow);
  padding: 5px 7px;
  cursor: pointer;
}

#copy-btn:hover {
  background-color: var(--pink);
}

.generator {
  display: flex;
}

#key-btn {
  height: 23px;
  width: 50%;
  border: none;
  margin-left: 5px;
  border-radius: 5px;
  color: var(--primary);
  background-color: var(--yellow);
}

#key-btn:hover {
  background-color: var(--pink);
}
</style>
