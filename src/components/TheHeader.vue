<template>
  <header class="header">
    <div class="container">
      <div class="logo">
        <img src="../assets/logo.png" alt="logo" />
      </div>
      <nav class="nav">
        <ul class="nav__list">
          <li><a href="#">About me</a></li>
          <li><a href="#">Relationships</a></li>
          <li><a href="#">Requirements</a></li>
          <li><a href="#">Users</a></li>
          <li><a href="#">Sign Up</a></li>
        </ul>
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
          <transition name="fade">
            <ul v-if="show" class="tablet-nav">
              <img src="@/assets/logo.png" width="135" height="20" />
              <hr>
              <li v-for="(item, id) in items" :key="id"><a href="">{{ item }}</a></li>
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
          a link to github/bitbucket repository.<span class="hide"
            >Please be patient, we consider and respond to every application
            that meets minimum requirements.<span class="block"
              >We look forward to your submission.Good luck!The photo has to
              scale in the banner area on the different screens</span
            ></span
          >
        </p>
        <button class="btn"><a href="#form">Sign up now</a></button>
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
  .nav {
    margin-left: 380px;
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
        color: #007bff ;
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
  .wrapper-content {
    padding-top: 170px;
    margin-left: 24.5%;
    font-size: 16px;
    width: 560px;
    color: #fff;
    span .block{
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
    padding-bottom: 33px;
    width: 529px;
    letter-spacing: 0.1px;

  }
  .btn {
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
      margin-right: 565px;
    }
    nav {
      position: absolute;
        margin-left: 482px;
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

      }
          .tablet-nav {
      display: flex;
      flex-direction: column;
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
        &:last-child{
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
@media only screen and (min-width: 320px) and (max-width: 480px) {
  .container {
    justify-content: space-between;
    padding: 20px 0 0px;
    max-width: 480px;
    .logo {
      padding-left: 14px;
    }
    .nav {
      position: absolute;
     margin-left: 60%;
      padding-right: 15px;
      .nav__list {
        display: none;
      }
          .menu {
          display: block;
          margin-right: 100px;
         }
          .burger {
    right: 288px;
    top: 11px;
        width: 290px;

      }
          .tablet-nav {
      display: flex;
      flex-direction: column;
      width: 280px;
      background-color: #fff;
      position: relative;
      right: 288px;
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
        &:last-child{
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
