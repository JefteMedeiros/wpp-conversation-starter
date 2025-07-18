<script setup>
  import { ref } from 'vue'

  const phoneNumber = ref('')
  const message = ref('')

  const handleWhatsAppRedirect = () => {
    const baseUrl = 'https://wa.me/'
    const formattedNumber = phoneNumber.value.replace(/\D/g, '')
    const encodedMessage = encodeURIComponent(message.value)
    const whatsappUrl = `${baseUrl}${formattedNumber}${message.value ? `?text=${encodedMessage}` : ''}`
    window.open(whatsappUrl, '_blank')
  }
</script>

<template>
  <div class="container">
    <div class="app-header">
      <h1>WPP Conversation Starter</h1>
      <p class="description">Simple app to start conversations without the need to save the contact</p>
    </div>

    <div class="form-container">
      <div class="input-group">
        <label for="number">Phone Number</label>
        <input 
          type="tel" 
          id="number"
          v-model="phoneNumber"
          placeholder="Enter phone number with country code"
        />
      </div>

      <div class="input-group">
        <label for="message">Message (Optional)</label>
        <textarea 
          id="message"
          v-model="message"
          placeholder="Type your message here..."
          rows="3"
        ></textarea>
      </div>

      <button @click="handleWhatsAppRedirect" class="start-chat-btn">
        Start Chat
      </button>
    </div>
  </div>
</template>
