<template>
  <div class="form-input">
    <div class="form-input__container-input">
      <div class="form-input__box-input">
        <input
          id="name"
          v-model="$parent.form.full_name"
          type="text"
          required
          minlength="1"
          :class="
            !$parent.form_valid.full_name ? 'form-input__invalid-input' : ''
          "
        />
        <label
          :style="!$parent.form_valid.full_name ? 'color: red;' : ''"
          for="name"
          >Insira seu nome</label
        >
        <span v-if="!$parent.form_valid.full_name">Nome inválido</span>
      </div>

      <div class="form-input__box-input">
        <input
          id="email"
          v-model="$parent.form.email"
          type="text"
          required
          :class="!$parent.form_valid.email ? 'form-input__invalid-input' : ''"
        />
        <label
          :style="!$parent.form_valid.email ? 'color: red;' : ''"
          for="email"
          >Seu e-mail</label
        >
        <span v-if="!$parent.form_valid.email">Nome inválido</span>
      </div>

      <div class="form-input__box-input">
        <the-mask
          id="phone"
          v-model="$parent.form.phone_number"
          :mask="['(##) ####-####', '(##) #####-####']"
          placeholder=" "
          type="tel"
          required
          :class="
            !$parent.form_valid.phone_number ? 'form-input__invalid-input' : ''
          "
        />
        <label
          :style="!$parent.form_valid.phone_number ? 'color: red;' : ''"
          for="phone"
          >Seu telefone</label
        >
        <span v-if="!$parent.form_valid.phone_number">Telefone inválido</span>
      </div>

      <div class="form-input__box-input">
        <input
          id="assunto"
          v-model="$parent.form.subject"
          type="text"
          required
          :class="
            !$parent.form_valid.subject ? 'form-input__invalid-input' : ''
          "
        />
        <label
          :style="!$parent.form_valid.subject ? 'color: red;' : ''"
          for="assunto"
          >O assunto</label
        >
        <span v-if="!$parent.form_valid.subject">Assunto inválido</span>
      </div>
    </div>
    <div class="form-input__box-input">
      <textarea
        id="msg"
        v-model="$parent.form.message"
        cols="30"
        rows="10"
        required
        class="form-input__text-area"
        :class="!$parent.form_valid.message ? 'form-input__invalid-input' : ''"
      ></textarea>
      <label :style="!$parent.form_valid.message ? 'color: red;' : ''" for="msg"
        >Deixe sua mensagem</label
      >
      <span v-if="!$parent.form_valid.message" style="bottom: -10px"
        >Mensagem inválida</span
      >
    </div>
  </div>
</template>

<script>
export default {
  name: 'FormInput',
}
</script>

<style lang="scss" scoped>
.form-input {
  &__box-input {
    position: relative;
    margin: 15px 0;
    input,
    textarea {
      width: 100%;
      border: 2px solid #000000;
      border-radius: 10px;
      height: 60px;
      padding-left: 13px;
      padding-top: 10px;
      font-size: 0.9em;
      font-weight: 600;
      outline-style: none;
      transition: all 0.2s ease-in-out;
      padding-right: 15px;
      &:valid + label,
      &:focus + label {
        top: 8px;
        font-weight: bold;
        font-size: 0.6em;
        transition: all 0.2s ease-in-out;
      }
      &:hover,
      &:focus {
        transition: all 0.2s ease-in-out;
        transform: scale(1.02);
      }
    }
    label {
      transition: all 0.2s ease-in-out;
      position: absolute;
      font-weight: 600;
      font-size: 0.9em;
      left: 15px;
      top: 23px;
    }
    textarea {
      height: 189px;
      padding-top: 25px;
      padding-left: 13px;
      padding-right: 15px;
    }
    span {
      position: absolute;
      bottom: -12px;
      left: 5px;
      color: red;
      font-size: 11px;
    }
  }
  &__invalid-input {
    border-color: red !important;
    color: red !important;
  }
}
@media (min-width: 768px) {
  .form-input {
    &__container-input {
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
    }
    &__box-input {
      input {
        width: 100%;
        min-width: 340px;
      }
    }
  }
}
@media (min-width: 1024px) {
  .form-input {
    &__box-input {
      input {
        min-width: 289px;
      }
    }
    span {
      bottom: -15px;
    }
  }
}
</style>
