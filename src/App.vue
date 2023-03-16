<template>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-lg-6">
        <div class="card shadow-lg">
          <div class="card-body">
            <h3 class="text-center mb-4">Login</h3>
            <form>
              <div class="mb-3">
                <label for="email" class="form-label">Email address</label>
                <input type="email" class="form-control" id="email" v-model="email" required>
              </div>
              <div class="mb-3">
                <label for="nickname" class="form-label">Nickname</label>
                <input type="text" class="form-control" id="nickname" v-model="nickname" required>
              </div>
              <div class="mb-3">
                <label for="password" class="form-label">Password</label>
                <input type="password" class="form-control" id="password" v-model="password" required>
              </div>
              <div class="d-grid gap-2">
                <button type="submit" class="btn btn-primary" @click.prevent="login">Submit</button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      email: '',
      nickname: '',
      password: ''
    }
  },
  methods: {
    login() {
      // 这里可以编写您的登录逻辑
      console.log('email:', this.email)
      console.log('nickname:', this.nickname)
      console.log('password:', this.password)
      //调用接口 json格式
      axios.post('/api/login', {  //这里的this.$http是在main.js中引入的axios
         email: this.email,
         nickname: this.nickname,
         password: this.password
       }).then(res => {
         console.log(res)
       })
    }
  }
}
</script>

<style>
.container {
  height: 100vh;
  background-color: #E5D5CC;
  display: grid;
  place-items: center;
}


.card {
  border: none;
  border-radius: 10px;
  background-color: #FFF7F2;
  display: inherit;
}

.card-body {
  padding: 40px;
  justify-content: center;
  display: inherit;
}

.form-label {
  color: #F9C74F;
  font-weight: 700;
  font-size: 1.2rem;
  display: inherit;
}

.form-control {
  height: 50px;
  font-size: 1.2rem;
  border: none;
  border-radius: 10px;
  background-color: #F5E5D6;
  display: inherit;
}

.form-control:focus {
  box-shadow: none;
}

.btn-primary {
  background-color: #F9C74F;
  border: none;
  border-radius: 10px;
  font-weight: 700;
  font-size: 1.2rem;
  margin-top: 2rem;
  padding: 0.75rem 1.5rem;
}

.btn-primary:hover {
  background-color: #F5A962;
}

.btn-primary:focus {
  box-shadow: none;
}
</style>
