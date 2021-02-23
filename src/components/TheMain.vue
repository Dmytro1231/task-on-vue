<template>
  <main class="main">
    <div class="block-acquitted">
      <div class="block-title">
        <h2 class="title">Let's get acquainted</h2>
      </div>
      <div class="wrapper-acquitted">
        <div class="img-block">
          <img src="../assets/man-picture.png" alt="man-picture" />
        </div>
        <div class="content">
          <h5>I am cool frontend developer</h5>
          <p>
            We will evaluate how clean your approach to writing CSS and
            Javascript code is.You can use any CSS and Javascript 3rd party
            libraries without any restricition.
            <span
              >If 3rd party css/javascript libraries are added to the project
              via bower/npm/yarn you will get bonus points.If you use any task
              runner (gulp/webpack) you will get bonus points as well.Slice
              service directory page PSD mockup into HTML5/CSS3.</span
            >
          </p>
          <button class="btn-flat"><a href="#form" class="black-link">Sing up now</a></button>
        </div>
      </div>
    </div>
    <div class="block-users">
      <div class="block-title">
        <h2 class="title title-users">Our cheerful users</h2>
        <p class="subtitle">Attention! Sorting users by registration date</p>
      </div>
      <div class="wrapper-users">
        <div class="users-item" v-for="user in users.users" :key="user.id">
          <img :src="user.photo" />
          <h3 class="user__name">{{ user.name}}</h3>
          <p class="user__position">{{ user.position}}</p>
          <span class="user__email">{{ user.email.slice(0, 20)}}...</span>
          <p class="user__phone">{{ user.phone}}</p>
        </div>
        <div class="load-users" v-for="newUser in newUserList.users" :key="newUser.id">
          <img :src="newUser.photo" />
          <h3 class="user__name">{{ newUser.name}}</h3>
          <p class="user__position">{{ newUser.position}}</p>
          <p class="user__email">{{ newUser.email.slice(0, 20)}}...</p>
          <p class="user__phone">{{ newUser.phone}}</p>
        </div>
      </div>
      <div class="wrap-btn">
        <button class="btn" v-on:click="getUsers">Show more</button>
      </div>
    </div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  name: 'TheMain',
  data () {
    return {
      users: [],
      newUserList: [],
      counter: 0
    }
  },
  methods: {
    getUsers (counter) {
      axios
        .get(`https://frontend-test-assignment-api.abz.agency/api/v1/users?page=${this.counter += 1}&count=5`)
        .then((response) => (this.newUserList = response.data))
        .catch((error) => {
          console.log(error)
        })
    }
  },
  mounted () {
    axios
      .get(
        'https://frontend-test-assignment-api.abz.agency/api/v1/users?page=1&count=5'
      )
      .then((response) => (this.users = response.data))
      .catch((error) => {
        console.log(error)
      })
  }
}
</script>

<style lang="scss" scoped>
$bg: #f9f9f3;
.block-acquitted {
  margin-bottom: 150px;
}
.title {
  margin-bottom: 58px;
}
.wrapper-acquitted {
  margin: 0 auto;
  display: flex;
  justify-content: center;

  .img-block {
    margin-left: 30px;
  }

  .content {
    width: 555px;
    margin-left: 50px;
    h5 {
      font-size: 24px;
      padding-bottom: 20px;
      letter-spacing: -0.3px;
    }
    p {
      display: grid;
      letter-spacing: 0.1px;
      span {
        margin-top: 30px;
        margin-bottom: 35px;
        letter-spacing: 0.1px;
      }
    }
    .btn-flat {
      cursor: pointer;
      border: none;
      outline: none;
      color: rgb(239, 91, 76);
      font-size: 16px;
      background-color: #fff;
      &:active {
        color: #d24335;
      }
      .black-link {
        color: #ef5b4c;
      }
    }
  }
}
.block-users {
  background-color: $bg;
  .title-users {
    margin-bottom: 15px;
  }
  .subtitle {
    margin-bottom: 25px;
    letter-spacing: 0.1px;
  }
  .wrapper-users {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: 1000px;
    margin-top: 100px;
    margin: 0 auto;
    text-align: center;
    img {
      border-radius: 50%;
    }
    .users-item {
      margin-right: 130px;
      h3 {
        widows: 200px;
      }
      img {
        border-radius: 50%;
        margin-bottom: 24px;
        margin-top: 50px;
      }
      .user__name {
        margin-bottom: 24px;
      }
      .user__position {
        margin-bottom: 15px;
      }
      .user__email {
        margin-bottom: 12px;
      }
    }
    .load-users {
      margin-top: 60px;
      margin-right: 145px;
      h3 {
        width: 200px;
      }
    }
  }
  .wrap-btn {
      padding-bottom: 160px;
    .btn {
    margin-left: 43%;
    margin-top: 40px;
    }
  }
  .btn-flat {
    margin-bottom: 160px;
    margin-left: 42%;
    margin-top: 40px;
  }
}
/* Tablets (вертикальная и горизонтальная) ----------- */
@media only screen and (min-width: 768px) and (max-width: 1024px) {
  .block-title {
    padding-top: 107px;
    .title {
      font-size: 40px;
    }
  }
  .wrapper-acquitted .img-block {
    img {
      width: 247px;
      height: 207px;
    }
  }
  .wrapper-acquitted .content {
    margin-left: 15px;
    width: 447px;

    p span {
      margin-bottom: 33px;
    }
  }
  .block-acquitted {
    margin-bottom: 115px;
  }
  .block-users {
    .wrapper-users {
      width: 100%;
      margin-top: 50px;
      display: flex;
      align-items: center;
      .users-item {
        margin-right: 50px;
        width: 195px;
      }
      .load-users {
        margin-right: 75px;
        img {
        border-radius: 50%;
        margin-bottom: 24px;
        margin-top: 50px;
      }
      .user__name {
        margin-bottom: 24px;
      }
      .user__position {
        margin-bottom: 15px;
      }
      .user__email {
        margin-bottom: 12px;
      }
      }
    }
    .wrap-btn {
      margin-left: 280px;
      margin-top: 24px;
      padding-bottom: 115px;
      .btn {
        margin-left: 0;
      }
    }
  }
}
// /* Smartphones (вертикальная и горизонтальная ориентация)
@media only screen and (min-width: 320px) and (max-width: 480px) {
  .block-acquitted {
    margin-bottom: 77px;
  }
  .block-title {
    padding-top: 70px;

    .title {
      font-size: 30px;
    }
  }
  .wrapper-acquitted {
    flex-direction: column;

    .img-block {
      margin-left: 10px;
      img {
        width: 289px;
        height: 243px;
      }
    }
    .content {
      margin-left: 15px;
      width: 340px;
      .btn-flat {
        margin-left: 120px;
      }
    }
  }
  .block-users {
  .title-users {
    margin-bottom: 8px;
  }
  .subtitle {
    margin-bottom: -14px;
    letter-spacing: -0.5px;
  }
  .wrapper-users {
    max-width: 480px;
    .users-item img {
      margin-bottom: 12px;
    }
    .users-item .user__position {
      margin-bottom: 10px;
    }
    .users-item .user__email {
      margin-bottom: 8px;
    }
    .users-item .user__name {
      margin-bottom: 12px;
    }
  }
  .wrap-btn .btn{
        margin-left: 66px;
    margin-top: 63px;
  }
}
}
</style>
