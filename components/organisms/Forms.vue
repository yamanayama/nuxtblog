<template lang="pug">
  //- form
  #form.form
    form#contact.netlify
      .form__block
        ul.form__list
          li.form__list__item
            label
              | 名前
            input(type="text" name="name" placeholder="Name")
          li.form__list__item
            label
              | メールアドレス
            input(type="email" name="email" placeholder="Email")
          li.form__list__item
            label
              | メッセージ
            textarea(type="text" name="message" placeholder="Message")
        button#submit(type="submit")
          | 送信する
</template>


<style lang="scss" scoped>
.form {
  &__block {
    margin: 0 auto;
    text-align: center;
    padding: 32px 24px;
    margin: 32px auto;
  }
}

label{
  display: block;
  font-size: 1.3rem;
  text-align: left;
  color:  $white;
}

input {
  margin-bottom: 24px;
}
textarea {
  height: 100px;
  margin-bottom: 24px;
}
input:first-of-type {
  margin-bottom: 24px;
}
input,
textarea {
  font-size: 1em;
  padding: 15px 10px 10px;
  border: none;
  background: $bg300;
  color: $white;
  border-radius: 5px;
  background-clip: padding-box;
  box-sizing: border-box;
  letter-spacing: 0.01em;
  width: 100%;
  // max-width: 900px;
}

:focus {
  border: 1px solid $primary;
}

::-webkit-input-placeholder {
  color: $text100;
}
:-moz-placeholder {
  color: $text100;
}
::-moz-placeholder {
  color: $text100;
}
:-ms-input-placeholder {
  color: $text100;
}
label.error {
  font-family: "Source Sans Pro", arial, sans-serif;
  font-size: 1em;
  display: block;
  padding-top: 24px;
  padding-bottom: 24px;
  background-color: #d89c9c;
  width: 80%;
  margin: auto;
  color: $white;
  -webkit-border-radius: 6px;
  -moz-border-radius: 6px;
  border-radius: 6px;
}
/* media queries */
@media (max-width: 700px) {
  label.error {
    width: 90%;
  }

  body {
    padding-top: 10px;
  }
}
.message {
  font-family: "Source Sans Pro", arial, sans-serif;
  font-size: 1.1em;
  display: none;
  padding-top: 10px;
  padding-bottom: 10px;
  background-color: #2abca7;
  width: 80%;
  margin: auto;
  color: $white;
  -webkit-border-radius: 6px;
  -moz-border-radius: 6px;
  border-radius: 6px;
}
//tab
@include md {
  .form {
    &__block {
    }
  }
}
</style>
