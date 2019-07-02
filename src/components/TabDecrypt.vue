<template>
  <div class="tab-decrypt">
    <p class="headlines">Personal Key:</p>
    <input inputmode="numeric" v-model="inputKey" placeholder="Enter your Key">

    <p class="headlines">Enter the Message:</p>
    <input id="decrypted-msg" v-model="inputMessage" placeholder="Enter your Message">

    <p class="headlines">Decrypted:</p>
    <input id="margin-input" :value="decrypt(inputMessage)" disabled>
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
    }
  }
};
</script>

<style>

</style>
