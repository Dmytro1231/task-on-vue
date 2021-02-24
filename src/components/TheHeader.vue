<template>
  <header class="header">
    <div class="container">
      <div class="logo">
        <img src="../assets/logo.png" alt="logo" />
      </div>
      <nav class="nav">
        <ul class="nav__list">
          <li><a href="#form">About me</a></li>
          <li><a href="#form">Relationships</a></li>
          <li><a href="#form">Requirements</a></li>
          <li><a href="#form">Users</a></li>
          <li><a href="#form">Sign Up</a></li>
        </ul>

        <!-- burger menu -->
        <div class="burger">
          <transition name="fade" mode="out-in">
            <i
              class="material-icons menu"
              v-if="!show"
              @click="show = !show"
              key="menu"
              >menu</i
            >
            <i
              class="material-icons clear"
              v-else
              @click="show = !show"
              key="clear"
              >clear</i
            >
          </transition>

          <!-- list of item nav -->
          <transition name="fade">
            <ul v-if="show" class="tablet-nav">
              <img src="@/assets/logo.png" width="135" height="20" />
              <hr />
              <li v-for="(item, id) in items" :key="id">
                <a href="#form">{{ item }}</a>
              </li>
            </ul>
          </transition>
        </div>
      </nav>
    </div>
    <div class="container-bg">
      <div class="wrapper-content">
        <h1>Test assignment for Frontend Developer position</h1>
        <p>
          We kindly remind you that your test assignment should be submitted as
          a link to github/bitbucket repository.<span class="hide">
            Please be patient, we consider and respond to every application that
            meets minimum requirements.<span class="block">
              We look forward to your submission.Good luck!The photo has to
              scale in the banner area on the different screens</span
            >
          </span>
        </p>
        <a href="#form" class="btn">Sign up now</a>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data () {
    return {
      items: [
        'About me',
        'Relationships',
        'Active item',
        'Sign up',
        'How it works',
        'Partnership',
        'Help',
        'Leave testimonial',
        'Contact us'
      ],
      show: false
    }
  }
}
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  justify-content: center;
  padding: 20px 0 15px;
  position: fixed;
  background-color: #fff;
  width: 100%;

  .logo {
    width: 44px;
    height: 32px;
  }

  .nav {
    margin-left: 476px;
    ul {
      font-size: 14px;
      display: flex;
      li:not(:last-child) {
        margin-right: 28px;
      }
      li a {
        color: #212529;
      }
      li a:active {
        color: #007bff;
      }
      li :hover {
        color: #ef5b4c;
      }
    }
    .menu {
      display: none;
    }
  }
}
.container-bg {
  background-image: url("../assets/banner-photo.jpg");
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  width: 100%;
  height: 100%;

  .wrapper-content {
    padding-top: 170px;
    padding-bottom: 108px;
    margin-left: 24.5%;
    font-size: 16px;
    width: 560px;
    color: #fff;
    span .block {
      display: block;
    }
  }

  h1 {
    padding-bottom: 23px;
    text-transform: uppercase;
    color: #fff;
    font-size: 50px;
    line-height: 1.08;
    width: 535px;
    letter-spacing: -0.8px;
  }

  p {
    line-height: 1.5;
    padding-bottom: 44px;
    width: 529px;
  }

  a .btn {
    margin-bottom: 113px;
    &:active {
      background-color: #d24335;
    }
  }
}

/* Tablets (вертикальная и горизонтальная) ----------- */
@media only screen and (min-width: 768px) and (max-width: 1024px) {
  .container {
    .logo {
      margin-right: 665px;
    }

    nav {
      position: absolute;
      margin-left: 960px !important;
      .nav__list {
        display: none;
      }
      .menu {
        display: block !important;
      }
      .burger {
        right: 288px;
        top: 11px;
        width: 290px;
        color: #1b4a8a;
      }
      .tablet-nav {
        display: flex;
        flex-direction: column;
        position: relative;
        right: 230px;
        width: 280px;
        background-color: #fff;
        img {
          margin-top: 13px;
          margin-bottom: 10px;
          margin-left: 15px;
        }
        li {
          padding-top: 30px;
          padding-left: 15px;
          padding-right: 112px;
          &:last-child {
            margin-bottom: 25px;
          }
        }
      }
    }
  }
  .container-bg {

    .wrapper-content {
      padding-top: 120px;
      margin-left: 30px;
      h1 {
        font-size: 40px;
        font-weight: normal;
        width: 420px;
      }
      p {
        width: 480px;
        span {
          display: contents;
        }
      }
    }
    .btn {
      margin-bottom: 70px;
    }
  }
}

// /* Smartphones (вертикальная и горизонтальная ориентация)
@media only screen and (min-width: 360px) and (max-width: 480px) {
  .container {
    justify-content: space-between;
    padding: 20px 0 0px;
    max-width: 480px;

    .logo {
      padding-left: 30px;
    }
    .nav {
      position: absolute;
      margin-left: 68%;
      padding-right: 15px;
      .nav__list {
        display: none;
      }
      .menu {
        display: block;
        margin-right: 100px;
      }

      // styling burger list
      .burger {
        color: #1b4a8a;
      }
      .tablet-nav {
        display: flex;
        flex-direction: column;
        width: 280px;
        background-color: #fff;
        position: relative;
        right: 326px;
        bottom: 47px;

        img {
          margin-top: 13px;
          margin-bottom: 10px;
          margin-left: 15px;
        }
        li {
          padding-top: 30px;
          padding-left: 15px;
          padding-right: 112px;
          &:last-child {
            margin-bottom: 25px;
          }
        }
      }
    }
  }

  .container-bg {

    .btn {
      margin-right: 243px;
      margin-bottom: 73px;
    }
    h1 {
      width: 310px;
    }
    .wrapper-content {
      padding-top: 120px;
      padding-left: 20px;
      margin-left: 0;
      text-align: center;
      h1 {
        font-size: 30px;
        font-weight: normal;
      }
      p {
        font-size: 16px;
        width: 318px;
        padding-bottom: 27px;
        .hide {
          display: none;
        }
      }
    }
  }
}
</style>
