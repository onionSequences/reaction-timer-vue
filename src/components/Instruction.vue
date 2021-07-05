<template>
  <div class="backdrop">
    <div class="modal">

      <h4 class="modal-title">Instruction</h4>

      <p>The rules are easy.</p>
      <p>After you press Play button on screen you will be see green box.</p>
      <p>Your goal is to press it as fast as you can.</p>
      <em>So let see how fast your reaction are.</em>

      <button class="modal-button" @click="closeModal">Get started</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    closeModal() {
      this.$emit('close')
      console.log('Pressed close')
    }
  }
}
</script>

<style>
.backdrop {
  background-color: grey;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
.modal {
  background-color: white;
  padding: 30px;
  border-radius: 10px;
  width: 300px;
  height: 300px;
  margin: 150px auto;
}
.modal-title {
  margin-top: 0;
}

.modal-button {
  margin-top: 50px;
}
</style>