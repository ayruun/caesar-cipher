<template>
    <div class="how-to">
        <h2>How to use:</h2>
        <p><b>Encrypt:</b><br> Select the "Encrypt" Tab. Enter a number lower than 9999 as a personal key. Then enter the message you want to encrypt. Copy the encrypted message. Sending the key and encrypted message seperately is recommended.</p>
        <p><b>Decrypt:</b><br> Select the "Decrypt" Tab. Enter the key and encrypted message you recieved. Read the revealed message.</p>
    </div>
</template>

<script>
export default {

}
</script>

<style>
    .how-to {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
    }

    .how-to h2 {
        align-self: center;
        margin: 15px 0;
    }

    .how-to p {
        font-size: 18px;
        margin: 15px 0;
        line-height: 150%;
    }
</style>
