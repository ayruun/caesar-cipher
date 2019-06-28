<template>
  <div class="tab-encrypt">
    <p class="headlines">Encryption Key:</p>
    <input v-model="inputKey" placeholder="Enter a Number lower than 9999">

    <p class="headlines">Enter a Message:</p>
    <input v-model="inputMessage" placeholder="Enter your Message">

    <p class="headlines">Encrypted:</p>
    <input :value="encrypt(inputMessage)" disabled>
    <input type="hidden" id="encrypted-msg" :value="encryptedMessage">
    <button @click="copyInput">Copy</button>
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
        return "PLEASE ENTER A KEY!";
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
.tab-encrypt {
  height: 50vh;
  width: 50vw;
  background: rgb(255, 255, 255);
  padding: 25px;
  box-shadow: 0px 0px 45px -12px rgba(0,0,0,0.75);
}

.headlines {
  font-size: 1.2em;
  margin: 5px;
}

input {
  margin-bottom: 25px;
  width: 100%;
}
</style>
