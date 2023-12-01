<template>
  <div class="container-fluid">
    <div class="row no-gutter">
      <div class="col-md-6 d-none d-md-flex bg-image"></div>

      <div class="login-form col-md-6">
        <div class="login d-flex align-items-center py-5">
          <div class="container">
            <div class="row">
              <div class="col-lg-10 col-xl-7 mx-auto">
                <img
                  src="../logo.png"
                  class="img-fluid mb-2"
                  alt="logezy-logo"
                  width="150"
                />
                <div class="mb-4">
                  <h4 class="mb-2 fw-bold">Login</h4>
                  <span>Welcome Back! Login to Access your Account</span>
                </div>
                <div class="error" v-if="msg.error">
                  <router-link to="/signup">SignUp</router-link>
                  <p class="text-danger">{{ msg.error }}</p>
                </div>

                <form @submit.prevent="login()" class="loginform">
                  <div class="mb-3">
                    <input
                      id="inputEmail"
                      type="email"
                      v-model="email"
                      placeholder="Email address"
                      autofocus="true"
                      class="form-control border-0 shadow-sm"
                    />
                    <div class="error" v-if="msg">
                      <span class="text-danger">{{ msg.email }}</span>
                    </div>
                  </div>
                  <div class="mb-3">
                    <input
                      id="inputPassword"
                      type="password"
                      v-model="password"
                      placeholder="Password"
                      required
                      class="form-control border-0 shadow-sm text-primary"
                    />
                    <div class="error">
                      <span class="text-danger" v-if="msg.password">{{
                        msg.password
                      }}</span>
                    </div>
                  </div>
                  <!-- <div class="form-check">
                    <input
                      id="customCheck1"
                      type="checkbox"
                      checked
                      class="form-check-input"
                    />
                    <label for="customCheck1" class="form-check-label"
                      >Remember password</label
                    >
                  </div> -->
                  <div class="my-4 d-flex justify-content-between">
                    <button
                      type="submit"
                      class="btn btn-primary btn-block text-capitalize shadow-sm"
                    >
                      Sign in
                    </button>
                    <!-- <div class="d-flex align-items-center">
                      Did you
                      <router-link class="ps-1" to="/forgotpassword">
                        Forget your password ?</router-link
                      >
                    </div> -->
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      msg: [],
    };
  },
  // watch: {
  //   email(value) {

  //     this.email = value;
  //     this.validateEmail();
  //   },
  //   password() {
  //     this.validatePassword();
  //   },
  // },
  methods: {
    async login() {
      const data = {
        email: this.email,
        password: this.password,
      };

      try {
        const response = await fetch(
          "https://logezy.onrender.com/merchant_login",
          {
            method: "POST",
            headers: {
              Accept: "application/json",
              "Content-Type": "application/json",
            },
            body: JSON.stringify(data),
          }
        );

        const jsonData = await response.json();

        if (jsonData.is_loged_in) {
          localStorage.setItem("token", jsonData.token);

          this.$router.push({ name: "Home" });
        }

        if (this.email != "merchant@gmail.com") {
          this.msg["email"] = "Please Enter Correct Email";
        } else {
          this.msg["email"] = "";
        }

        if (this.password != "merchant@123") {
          this.msg["password"] = "Please Enter Correct Password";
        }
      } catch (error) {
        console.log(error);
      }
    },

    // validateEmail(value) {
    //   if (value == null) {
    //     this.msg["email"] = "Please Enter Email";
    //     console.log(this.msg["email"]);
    //   } else {
    //     this.msg["email"] = "Please Enter Correct Email";
    //   }
    // },
  },

  mounted() {
    const token = localStorage.getItem("token");
    if (token) {
      this.$router.push({ name: "Home" });
    }
  },
};
</script>

<style scoped>
.login,
.image {
  min-height: 100vh;
}

.bg-image {
  background-image: url("src/assets/login-split.jpg");
  background-size: cover;
  background-position: center center;
  margin-top: 90px;
}
.form-control {
  background-color: #f7f5f4;
  padding: 0.4rem 0.75rem;
}

.btn-primary {
  border: none;
}
</style>
