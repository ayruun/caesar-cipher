<template>
  <div class="tab-decrypt">
    <p class="headlines">Encryption Key:</p>
    <input v-model="inputKey" placeholder="Enter your Key">

    <p class="headlines">Enter the Message:</p>
    <input v-model="inputMessage" placeholder="Enter your Message">
    <button @click="pasteInput">Paste</button>

    <p class="headlines">Decrypted:</p>
    <input :value="decrypt(inputMessage)" disabled>
    <input type="hidden" id="encrypted-msg" :value="decryptedMessage">
    
  </div>
</template>

<script>
export default {
  name: "TabDecrypt",
  data() {
    return {
      inputKey: "",
      inputMessage: "",
      decryptedMessage: ""
    };
  },
  methods: {
    decrypt(input) {
      if (!parseInt(this.inputKey)) {
        return "PLEASE ENTER YOUR KEY!";
      } else if (parseInt(this.inputKey) > 9999) {
        return "Key has to be lower than 9999";
      }

      this.decryptedMessage = input
        .split("")
        .map(el => {
          let charCode = el.charCodeAt() - parseInt(this.inputKey);
          return String.fromCharCode(charCode);
        })
        .join("");

      return this.decryptedMessage;
    },
    pasteInput() {
      console.log("paste");
    }
  }
};
</script>

<style>
.tab-decrypt {
  height: 50vh;
  width: 50vw;
  background: grey;
  padding: 25px;
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
