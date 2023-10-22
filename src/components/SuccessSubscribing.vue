<script setup>
const props = defineProps(['message'])

const goToHome = () => {
  window.location.href = '/'
}
</script>

<template>
  <section class="container">
    <figure>
      <img src="../assets/images/icon-success.svg" alt="icon success" />
    </figure>
    <h1 class="success-title">Thanks for subscribing!</h1>
    <p class="success-text">
      A confirmation email has been sent to <strong>{{ props.message.value }}</strong
      >. Please open it and click the button inside to confirm your subscription.
    </p>
    <button @click="goToHome" type="submit">Dismiss message</button>
  </section>
</template>

<style scoped>
.container {
  width: 504px;
  height: 520px;
  padding: 3rem 4rem;
  display: flex;
  flex-direction: column;
  background-color: var(--white);
  border-radius: 2.2rem;
  color: var(--dark-slate-grey);
}
.success-title {
  margin-top: 2.3rem;
  font-size: 3.5rem;
  font-weight: 500;
  line-height: 3.5rem;
  letter-spacing: 0.01rem;
}
.success-text {
  margin-top: 1.5rem;
  line-height: 1.5rem;
}

button {
  width: 376px;
  height: 56px;
  margin-top: 2.45rem;
  padding-top: 0.1rem;
  font-size: 0.99rem;
  letter-spacing: -0.003rem;
  color: var(--white);
  border-radius: 8px;
  border: none;
  background-color: hsl(234, 29%, 20%);
  cursor: pointer;
  position: relative;
}

button::before {
  content: 'Dismiss message';
  position: absolute;
  top: 0;
  right: 0;
  width: 100%;
  height: 100%;
  padding-top: 0.1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
  background: linear-gradient(90deg, rgba(255, 83, 123, 1) 0%, rgba(255, 105, 58, 1) 100%);
  box-shadow: 0 10px 25px hsla(4, 100%, 67%, 0.4);
  opacity: 0;
  transition: opacity 0.3s;
}

button:hover::before {
  opacity: 1;
}

@media screen and (max-width: 860px) {
  .container {
    width: 80%;
    height: 100%;
    min-height: 500px;
    margin: 0 auto;
    padding: 3rem;
    border-radius: 0;
  }

  button {
    width: 100%;
    margin-top: auto;
    flex-shrink: 0;
  }
}

@media screen and (max-width: 680px) {
  .container {
    width: 100%;
  }
}

@media screen and (max-width: 480px) {
  .container {
    padding: 3rem 1rem;
  }
  .success-title {
    font-size: 2.5rem;
    line-height: 2.8rem;
  }
}
</style>
