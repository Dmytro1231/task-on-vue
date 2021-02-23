<template>
  <div class="block-title">
    <h2 class="title title-form">Register to get a work</h2>
    <p class="subtitle">
      Attention! After successful registration and alert, update the <span>list of
      users in the block from the top</span>
    </p>
  </div>
  <form class="form" @submit.prevent="submitHandler" method="post">
    <label for="name" :class="{invalid: errors.name}"
      >Name
      <input type="text" placeholder="Your name" v-model.trim="users.name"/>
    </label>
    <small v-if="errors.name">{{ errors.name }}</small>
    <label for="email" :class="{invalid: errors.email}"
      >Email
      <input type="email" placeholder="Your email" v-model.trim="users.email"/>
    </label>
    <small v-if="errors.email">{{ errors.email }}</small>
    <label for="phone" :class="{invalid: errors.phone}"
      >Phone number
      <input type="tel" placeholder="+380 XX XXX XX XX" v-model.number="users.phone"/>
    </label>
     <small v-if="errors.phone">{{ errors.phone }}</small>
    <span>Enter phone number in open format</span>

    <div class="radio-wrapper">
      <p>Select your position</p>
      <div class="radio">
        <input
          class="custom-radio"
          type="radio"
          id="color-1"
          name="color"
          value="Frontend-developer"
          v-model="users.position"
        />
        <label for="color-1" class="select-label">Frontend developer</label>
      </div>

      <div class="radio">
        <input
          class="custom-radio"
          type="radio"
          id="color-2"
          name="color"
          value="Backend-developer"
          v-model="users.position"
        />
        <label for="color-2" class="select-label">Backend developer</label>
      </div>

      <div class="radio">
        <input
          class="custom-radio"
          type="radio"
          id="color-4"
          name="color"
          value="Designer"
          v-model="users.position"
        />
        <label for="color-4" class="select-label">Designer</label>
      </div>

      <div class="radio">
        <input
          class="custom-radio"
          type="radio"
          id="color-5"
          name="color"
          value="QA"
          v-model="users.position"
        />
        <label for="color-5" class="select-label">QA</label>
      </div>
         <small v-if="errors.position">{{ errors.position }}</small>
    </div>

    <div class="field__wrapper">
      <input
        name="file"
        type="file"
        id="field__file-2"
        class="field field__file"
        multiple
      />

    <p>Photo</p>
      <label class="field__file-wrapper" for="field__file-2">
        <div class="field__file-fake" :class="{invalid: errors.fileChoose}">Upload your photo</div>
        <div class="field__file-button">Browse</div>
      </label>
    </div>
    <button class="btn form-btn"><a name="form">Sign up now</a></button>
  </form>
  <hr>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      arrUsers: [],
      token: '',
      users: {
        name: '',
        email: '',
        phone: '',
        position: 'no choose'
      },
      errors: {
        name: null,
        email: null,
        phone: null,
        fileChoose: null
      }
    }
  },
  methods: {
    formIsValid () {
      let isValid = true

      if (this.users.name.length === 0) {
        this.errors.name = 'Error'
        isValid = false
      } else if (this.users.email.length === 0) {
        this.errors.email = 'Error'
        isValid = false
      } else if (this.users.phone.length === 0) {
        this.errors.phone = 'Error'
        isValid = false
      } else if (this.users.position === 'no choose') {
        this.errors.position = 'Error'
        isValid = false
      } else {
        this.errors.name = null
        this.users.name = ''
        this.errors.email = null
        this.users.email = ''
        this.errors.phone = null
        this.users.phone = ''
        this.errors.position = false
        this.users.position = false
      }

      return isValid
    },
    submitHandler () {
      if (this.formIsValid()) {
        // 45
        // this.arrUsers.push(this.name, this.email, this.phone, this.position)
        // const str = JSON.stringify(this.users);
        // axios.post('https://frontend-test-assignment-api.abz.agency/api/v1/users', str)
        // .then((result) => {
        //   console.log(result);
        // })
        // .catch((error) => {
        //   console.log(error);
        // })
        axios.get('https://frontend-test-assignment-api.abz.agency/api/v1/token')
          .then((result) => {
            this.token = result.data.token
            localStorage.setItem('user-token', this.token)
          }).catch((error) => {
            console.log(error)
            localStorage.removeItem('user-token')
          })
      }
    }
  },
  displayUsers () {

  }
}
</script>

<style lang="scss" scoped>
.title-form {
  margin-bottom: 12px;
}
form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 30px;
  font-family: 'PT Sans', sans-serif;
  span {
    margin-right: 262px;
    position: relative;
    bottom: 13px;
    font-size: 12px;
    font-family: 'Open Sans', sans-serif;
    line-height: 1.2;
  }
  // Валидация формы (красный текст,input)
  small {
    color: red;

    position: relative;
    right: 215px;
    bottom: 20px;

  }
  .invalid input {
    border-color: red;
  }
}
label {
  display: flex;
  flex-direction: column;
  margin-bottom: 22px;
  input {
   width: 467px;
    height: 38px;
    border-width: 1px;
    border-color: rgb(206, 212, 218);
    border-style: solid;
    border-radius: 4px;
    background-color: rgb(255, 255, 255);
    margin-top: 10px;
    padding-top: 14px;
    padding-bottom: 14px;
    padding-left: 14px;
    outline: none;
  }
   input:active {
     border-color: blue;
     box-shadow: 0px 0px 8px 0px rgba(45, 125, 186, 0.2);
   }
}
.radio-wrapper {
  margin-top: 9px;
    margin-right: 307px;
  p {
    margin-bottom: 32px;
  }
}
.custom-radio {
  position: absolute;
  z-index: -1;
  opacity: 0;
}
.custom-radio + label {
  display: inline-flex;
  align-items: center;
  user-select: none;
  display: block;
}
.custom-radio + label::before {
  content: "";
  display: inline-block;
  width: 1em;
  height: 1em;
  flex-shrink: 0;
  flex-grow: 0;
  border: 1px solid #adb5bd;
  border-radius: 50%;
  margin-right: 0.5em;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: 50% 50%;
}
.custom-radio:not(:disabled):not(:checked) + label:hover::before {
  border-color: #b3d7ff;
}
.custom-radio:not(:disabled):active + label::before {
  background-color: #b3d7ff;
  border-color: #b3d7ff;
}
.custom-radio:focus:not(:checked) + label::before {
  border-color: #80bdff;
}
.custom-radio:checked + label::before {
  border-color: #0b76ef;
  background-color: #0b76ef;
  background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='-4 -4 8 8'%3e%3ccircle r='3' fill='%23fff'/%3e%3c/svg%3e");
}
.select-label {
  position: relative;
  bottom: 14px;
  margin-bottom: 8px;
}

.field__wrapper {
  width: 470px;
  position: relative;
  margin: -7px 0;
  text-align: center;
  p {
      text-align: left;
      padding-bottom: 15px;
  }
}

.field__file {
  opacity: 0;
  visibility: hidden;
  position: absolute;
}

.field__file-wrapper {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  flex-wrap: nowrap;
}

.field__file-fake {
 width: 465px;
height: 36px;
  display: flex;
  align-items: center;
  padding: 0 15px;
  border-width: 1px;
  border-color: rgb(206, 212, 218);
  border-style: solid;
  border-radius: 4px;
  background-color: rgb(255, 255, 255);
}

.field__file-button {
     width: 81px;
  height: 36px;
 border-width: 1px;
  border-color: rgb(212, 217, 222);
  border-style: solid;
  background-color: rgb(248, 247, 245);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  padding-top: 13px;
  padding-left: 17px;
  padding-bottom: 13px;
  padding-right: 17px;
}
.form-btn {
    margin-bottom: 165px;
    margin-top: 25px;
}
/* Tablets (вертикальная и горизонтальная) ----------- */
@media only screen and (min-width: 768px) and (max-width: 1024px) {
  .block-title {
    padding-top: 107px;
    .title-form {
      font-size: 40px;
    }
  }
  form {
    .form-btn {
      margin-bottom: 115px;
    }
  }
}
// /* Smartphones (вертикальная и горизонтальная ориентация)
@media only screen and (min-width : 320px) and (max-width : 480px) {
  .block-title {
    padding-top: 60px;
    h2 {
      font-size: 30px;
    }
    .subtitle {
      display: block;
    }
  }
  .form {
    align-items: flex-start;
    margin-left: 15px;

    label input {
       width: 328px;
       height: 36px;
    }
    span {
      margin-right: 0;
    }
    .radio-wrapper {
      margin-right: 0;
    }
    .field__wrapper {
      width: 328px;
    }
    .form-btn {
      margin-left: 57px;
      margin-bottom: 77px;
    }
  }
}
</style>
