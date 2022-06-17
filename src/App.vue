<script>
import LoginVue from "./Login.vue";
export default {
  name: "App",
  components: {
    LoginVue
  },
  data() {
    return {
      image: "src/assets/logo.png",
      imag: "src/assets/onboard.svg",
      pwdvisiblity: "password",
      icon: "bi bi-eye-slash",
      userData: [
        {
          email: "vishwajith@cyware.com",
          password: "Test",
        },
        {
          email: "sample@cyware.com",
          password: "Test",
        },
        {
          email: "another@cyware.com",
          password: "Test",
        },
      ],
      formcon: "form-control emailinp",
      formpwd: "form-control pwdinp",
      entryToken: 0,
    };
  },
  methods: {
    visiblity() {
      if (this.pwdvisiblity === "password") {
        this.pwdvisiblity = "text";
        this.icon = "bi bi-eye-fill";
      } else {
        this.pwdvisiblity = "password";
        this.icon = "bi bi-eye-slash";
      }
    },
    submit() {
      let email = document.getElementById("floatingInput").value;
      let pwd = document.getElementById("floatingPassword").value;
      this.userData.forEach((element) => {
        if (element.email === email) {
          this.entryToken = 1;
          if (element.password === pwd) {
            this.entryToken = 2;
          }
        }
      });
      if (this.entryToken === 0) {
        this.formcon = "form-control is-invalid emailinp";
        this.formpwd = "form-control is-invalid pwdinp";
      } else if (this.entryToken === 1) {
        this.formcon = "form-control emailinp";
        this.formpwd = "form-control is-invalid pwdinp";
        this.entryToken = 0;
      } else {
        this.formcon = "form-control emailinp";
        this.formpwd = "form-control pwdinp";
        alert("Valid User");
        this.entryToken = 0;
      }
    },
  },
};
</script>

<template>
  <div class="row home">
    <div class="col-7 container left">
      <nav class="navbar">
        <a class="navbar-brand">
          <img :src="image" alt="logo" width="100" />
        </a>
      </nav>
      <h1 class="first">Welcome to</h1>
      <h1 class="second">Cyware Fusion Threat Response</h1>
      <p>
        A threat response automation platform that combines cyber fusion,
        advanced orchestration, and automation to stay ahead of increasingly
        sophisticated cyber threats affecting enterprises in real-time.
      </p>
      <img class="bgimg" :src="imag" />
    </div>
    <div class="col-5 container right">
      <div class="view">
        <h2>👋 Hello!</h2>
        <p class="gm">Good Evening!</p>
        <p>Lets get you started.</p>
        <form class="form">
          <div class="form-floating">
            <input type="email" :class="formcon" id="floatingInput" placeholder="name@example.com" />
            <label for="floatingInput">Email address</label>
          </div>
          <div class="form-floating pwd">
            <input
              :type="pwdvisiblity"
              :class="formpwd"
              id="floatingPassword"
              placeholder="Password"
            />
            <span>
              <i :class="icon" @click="visiblity" />
            </span>
            <label for="floatingPassword">Password</label>
          </div>
          <div class="redirects">
            <div class="forgot">
              <h5>Forgot Password?</h5>
            </div>
            <div class="login">
              <button type="button" class="btn lgnbtn" @click="submit">Login →</button>
            </div>
          </div>
          <br />
          <br />
          <div class="choice">
            <p>OR</p>
          </div>
          <div class="google">
            <button>
              <img
                alt="Google Logo"
                src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Google_%22G%22_Logo.svg/24px-Google_%22G%22_Logo.svg.png?20210618182606"
                decoding="async"
                width="24"
                height="24"
                srcset="https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Google_%22G%22_Logo.svg/36px-Google_%22G%22_Logo.svg.png?20210618182606 1.5x, https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Google_%22G%22_Logo.svg/48px-Google_%22G%22_Logo.svg.png?20210618182606 2x"
                data-file-width="24"
                data-file-height="24"
              />Sign in with Google
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<style>
div {
  padding: 0;
  margin: 0;
}
body {
  height: 100%;
}
.home {
  padding: 0;
  height: 100%;
}
.home .left {
  padding: 20px 25px 25px 45px;
}
.home .left h1 {
  font-size: 30px;
}
.home .left .first {
  font-weight: 400;
  margin: 20px 0 0 0;
  color: #42526e;
}
.home .left .second {
  font-weight: 700;
}
.home .left p {
  margin: 20px 20px 10px 0;
  max-width: 560px;
  color: #42526e;
  line-height: 25px;
  font-size: 14px;
}
.home .left .bgimg {
  width: 100%;
}
.home .right {
  background: #00a27b;
  padding: 50px;
  margin: 0;
  display: block;
}
.right .view {
  padding: 40px;
  background: #fff;
  border-radius: 10px;
  margin-top: 20%;
}
.right .view .gm {
  font-weight: 700;
  margin-top: 15px;
  margin-bottom: 10px;
}
.right .view .form .pwd {
  position: relative;
}
.right .view .form .pwd span {
  position: absolute;
  right: 35px;
  top: 30%;
  cursor: pointer;
}
.right .view .form .emailinp {
  margin-top: 30px;
}
.right .view .form .pwdinp {
  margin-top: 25px;
}
.right .view .redirects {
  margin-top: 20px;
  margin-bottom: 20px;
}
.right .view .redirects .forgot {
  float: left;
  width: 50%;
  margin-top: 10px;
}
.right .view .redirects .forgot h5 {
  font-size: 15px;
  color: #00a27b;
}
.right .view .redirects .login {
  float: right;
  width: 50%;
  text-align: end;
}
.right .view .redirects .login .lgnbtn {
  background: #00a27b;
  color: #fff;
  font-size: 18px;
  font-weight: 700;
  padding: 7px 20px 7px 20px;
  border-radius: 20px;
  box-shadow: 0.1px 0.1px 0.2em #888;
}
.right .view .choice {
  float: none;
  width: 100%;
  text-align: center;
  color: #ccc;
}
.right .view .google {
  padding: auto auto;
  text-align: center;
}
.right .view .google button {
  padding: 15px 25px;
  border-radius: 5px;
  background-color: #fff;
  border: 0.5px solid #eee;
  box-shadow: 0.1px 0.1px 0.2em #888;
}
.right .view .google button img {
  margin-right: 10px;
}
</style>
