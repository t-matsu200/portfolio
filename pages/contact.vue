<template>
  <section role="main" class="contact">
    <div class="narrow-container">
      <h1>Contact</h1>
      <p>{{ $t("CONTACT_FORM_LABEL") }}</p>
      <form netlify
        name="contact"
        method="post"
        data-netlify="true"
        data-netlify-honeypot="bot-field"
      >
        <input type="hidden" name="form-name" value="contact">
        <div class="flexbox">
          <div>
            <label for="name">Name</label>
            <span>
              <input
                :value="name"
                @input="ev => name = ev.target.value"
                type="text"
                name="name"
                size="40"
                autocomplete="name"
              >
              <p v-show="validation.nameMsg" class="not-valid">
                {{ validation.nameMsg }}
              </p>
            </span>
            <label for="email">Email</label>
            <span>
              <input
                :value="email"
                @input="ev => email = ev.target.value"
                type="email"
                name="email"
                size="40"
                autocomplete="email"
              >
              <p v-show="validation.emailMsg" class="not-valid">
                {{ validation.emailMsg }}
              </p>
            </span>
          </div>
          <div>
            <label for="message">Message</label>
            <span>
              <textarea
                :value="message"
                name="message"
                cols="41"
                rows="11"
              ></textarea>
              <p v-show="validation.messageMsg" class="not-valid">
                {{ validation.messageMsg }}
              </p>
            </span>
          </div>
        </div>
        <button class="btn">
          Send
        </button>
      </form>
    </div>
  </section>
</template>

<script lang="ts">
import { Component, Vue, Watch } from 'nuxt-property-decorator'

@Component
export default class Contact extends Vue {
  private name: string = ''
  private email: string = ''
  private message: string = ''
  private validation = {
    nameMsg: '',
    emailMsg: '',
    messageMsg: ''
  };

  @Watch('name', { deep: true, immediate: true })
  public nameChange(v: string): void {
    if (v) {
      this.validateName()
    }
  }

  @Watch('email', { deep: true, immediate: true })
  public emailChange(v: string): void {
    if (v) {
      this.validateEmail()
    }
  }

  @Watch('message', { deep: true, immediate: true })
  public messageChange(v: string): void {
    if (v) {
      this.validateMessage()
    }
  }

  private validateName(): boolean {
    if (!this.name.trim()) {
      this.validation.nameMsg = 'The Name field is required'
    } else {
      this.validation.nameMsg = ''
    }

    if (this.validation.nameMsg) {
      return true
    }
    return false
  }

  private validateMessage(): boolean {
    if (!this.message.trim()) {
      this.validation.messageMsg = 'The Message field is required'
    } else if (this.message.length < 100) {
      this.validation.messageMsg =
        'The Message field must be at least 100 characters'
    } else {
      this.validation.messageMsg = ''
    }

    if (this.validation.messageMsg) {
      return true
    }
    return false
  }

  private validateEmail(): boolean {
    if (!this.email.trim()) {
      this.validation.emailMsg = 'The Email field is required'
    } else if (!this.validEmail(this.email)) {
      this.validation.emailMsg = 'The Email field must be a valid email'
    } else {
      this.validation.emailMsg = ''
    }

    if (this.validation.emailMsg) {
      return true
    }
    return false
  }

  private validEmail(email: string): boolean {
    const re =
      /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
    return re.test(email)
  }
}
</script>

<style scoped>
.contact {
  text-align: center;
  min-height: calc(var(--vh, 1vh) * 100);
}

.contact h1 {
  font-size: 4.375rem;
  font-family: Sofia, cursive;
}

.contact .narrow-container {
  padding-top: 20%;
  padding-bottom: 20%;
}

.contact p {
  text-align: left;
}

form {
  margin-top: 5%;
}

form button,
form input,
form textarea {
  font-size: 1rem;
  font-family: inherit;
}

form label {
  display: block;
  margin-bottom: 5px;
  text-align: left;
}

form input[type="email"],
form input[type="text"],
form textarea {
  background: #fff;
  border: none;
  padding: 10px;
  border-radius: 5px;
  -webkit-appearance: none;
  width: 100%;
  margin-bottom: 10px;
}

form button,
form input[type="submit"] {
  border: none;
  cursor: pointer;
  -webkit-appearance: none;
}

.not-valid {
  font-size: 0.75rem;
  line-height: 1.5;
  position: relative;
  background: hsla(0, 0%, 100%, 0.5);
  padding: 10px 5px 5px;
  margin-top: -18px;
  border-radius: 0 0 5px 5px;
}

form textarea {
  height: 130px;
}

.btn {
  color: #fff;
  border-radius: 5px;
  text-decoration: none;
  background: #0bd;
  box-shadow: 0 1px 3px rgb(0 0 0 / 30%);
  position: relative;
  display: inline-block;
  top: -2px;
  padding: 10px;
  width: 100%;
  text-align: center;
  margin-top: 15px;
  transition: 0.3s;
}

.btn:disabled {
  background: #ccc;
}

@media (min-width: 1080px) {
  .container,
  .narrow-container {
    padding-right: 0;
    padding-left: 0;
  }
}

@media (min-width: 860px) {
  .contact .narrow-container {
    padding-top: 10%;
    padding-bottom: 0;
  }

  .contact p {
    text-align: center;
  }

  .contact .flexbox {
    justify-content: space-between;
  }

  .contact .flexbox div:first-child {
    margin-right: 3%;
  }

  form input[type="email"],
  form input[type="text"] {
    max-width: 450px;
  }

  .contact p {
    text-align: center;
  }

  form textarea {
    min-width: 420px;
  }

  .btn {
    width: auto;
    padding: 10px 20px;
  }
}
</style>
