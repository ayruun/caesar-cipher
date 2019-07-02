<template>
  <div class="tab-encrypt">
    <p class="headlines">Encryption Key:</p>
    <input v-model="inputKey" placeholder="Enter a Number lower than 9999">

    <p class="headlines">Enter a Message:</p>
    <input v-model="inputMessage" placeholder="Enter your Message to decrypt">

    <p class="headlines">Encrypted:</p>
    <input :value="encrypt(inputMessage)" disabled>
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
        return "PLEASE ENTER A KEY FIRST!";
      } else if (parseInt(this.inputKey) > 9999) {
        return "Key has to be lower than 9999";
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
</style>
