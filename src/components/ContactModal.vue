<template>
  <div
      class="modal-container"
  >
    <div class="overdrop" @click="closeHandler"></div>
    <div class="modal">
      <button class="close-button" @click="closeHandler"><img src="/icons/close.svg" alt="close icon"></button>
      <form @submit.prevent="submit" @reset="onReset">
        <div class="input-container">
          <label>IMIĘ</label>
          <input
              placeholder="- wpisz -"
              v-model="name"

          />
        </div>
        <div class="input-container">
          <label>NAZWISKO</label>
          <input
              placeholder="- wpisz -"
              v-model="surname"

          />
        </div>
        <div class="input-container">
          <label>ADRES E-MAIL</label>
          <input
              placeholder="- wpisz -"
              v-model="email"

          />
        </div>
        <div class="input-container">
          <div class="checkbox-container">
            <input type="checkbox" v-model="accept">
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore
              et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip
              ex ea commodo consequat.</p>
          </div>
        </div>
        <button class="submit-button">WYŚLIJ</button>
        <div v-if="!isValid" class="error-message">Proszę uzupełnić wymagane pola!</div>
      </form>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  props: ['closeHandler'],
  data() {
    return {
      isValid: true,
      name: "",
      surname: "",
      email: "",
      accept: false
    };
  },
  computed: {
    formValid() {
      const {name, surname, email, accept} = this;
      return (
          name.length > 0 &&
          surname.length > 0 &&
          /(.+)@(.+){2,}\.(.+){2,}/.test(email) &&
          accept === true
      );
    },
  },
  methods: {
    submit() {
      if (!this.formValid) {
        this.isValid = false;
        return;
      }
      this.isValid = true;
      const {name, surname, email, accept} = this;
      const messageToSend = {
        name,
        surname,
        email,
        accept
      };
      console.log(JSON.stringify(messageToSend));
    },
  },
};
</script>

<style lang="scss">
.modal-container {
  z-index: 3;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
.overdrop {
  background-color: transparentize($color-secondary, 0.5);
  position: absolute;
  z-index: 3;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}

.modal {
  position: relative;
  z-index: 4;
  width: 80%;
  max-width: 500px;
  background: $color-primary;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 3em 8em;
  border-radius: 1.2em;
  box-shadow: 0 0 99px $color-accent--light;

  .close-button {
    background: 0;
    border: 0;
    position: absolute;
    top: 1em;
    right: 1em;
    font-size: 1.5em;
    font-weight: 700;
    color: $color-secondary;

    &:hover {
      cursor: pointer;
    }
  }

  .input-container {
    display: flex;
    flex-direction: column;
    margin: 1em;

    label {
      letter-spacing: .2em;
      color: $color-secondary;
    }

    input {
      padding: .8em;
      border: 1px solid $color-secondary;
      border-radius: .7em;
      letter-spacing: .2em;
      color: $color-secondary;
      margin: .5em 0;
    }
    input::placeholder {
      color: $color-secondary;
    }

    .checkbox-container {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      gap: 10px;
      font-size: .1em;

      input:checked{
        &:before {
          background: 0;
        }
      }
    }
  }

  .submit-button {
    position: relative;
    width: 100%;
    padding: 1em;
    background: $color-accent;
    color: $color-primary;
    letter-spacing: .1em;
    font-weight: 400;
    font-size: 1.1em;
    border: 0;
    border-radius: .5em;
    cursor: pointer;
  }
}

.error-message {
  margin: 1em 0;
  color: $color-accent;
  text-align: center;
}
</style>
