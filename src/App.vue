<template>
  <div class="register">
    <h1>Đăng kí</h1>
    <form @submit="handleSubmit">
      <div class="form-input">
      <label>Họ và Tên</label>
      <input type="text" v-model="name" @change="hanldeForcus"  placeholder="VD: Nguyễn Văn A" />
      <span :class="isRequieName ? 'form-message' : 'form-completed' ">Nhập họ tên là bắt buộc</span>
      </div>
      <div class="form-input">
      <label>Email:</label>
      <input type="text" v-model="email" placeholder="VD: abc@gmail.com" />
      <span :class="isRequieEmail ? 'form-message' : 'form-completed' ">Nhập email là bắt buộc</span>
      </div>
      <div class="form-input">
      <label>Nhập password:</label>
      <input type="password" v-model="password" placeholder="Nhập password" />
      <span :class="isRequiePassword ? 'form-message' : 'form-completed' ">Nhập mật khẩu</span>
      </div>
      <div class="form-input">
      <label>Nhập lại password:</label>
      <input type="password" v-model="confirmPassword" placeholder="Nhập lại password" />
      <span :class="isRequieConfirm ? 'form-message' : 'form-completed' ">Mật khẩu không khớp</span>
      </div>   
      <button >Đăng kí</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      name:"",
      email:"",
      password:"",
      confirmPassword:"",
      isRequieEmail: false,
      isRequieName: false,
      isRequiePassword: false,
      isRequieConfirm: false,
      regex : /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(.\w{2,3})+$/
    }
  },
  methods: {
    handleSubmit: function(e){
      e.preventDefault();
      if (this.name === ''){
        console.log("Thiếu tên")
        return this.isRequieName = true
      } else if (this.email === '' || this.regex[this.email] ){
        console.log("Thiếu email")
        return this.isRequieEmail = true
      } else if (this.password === ''){
        console.log("Thiếu password")
        return this.isRequiePassword = true
      } else if (this.password !== this.confirmPassword){
        console.log("Mật khẩu không khớp")
        return this.isRequieConfirm = true
      } else {
        console.log({
          name:this.name,
          email:this.email,
          password:this.password,
        })
      }
    },
    hanldeForcus : function() {
      return this.isRequieEmail = false
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,500;0,700;1,100&display=swap');
*{
  padding:0;
  margin: 0;
  box-sizing: border-box;
}
html{
 background: #f1f1f1;
    min-height: 100vh;
    display: flex;
    justify-content: center;
}
#app {
  font-family: 'Roboto', sans-serif;
}
.register{
  align-items: center;
  display: inline-flex;
  flex-direction: column;
  margin: 20px; 
  background-color: white;
}
h1{
  font-size: 1.6rem;
  font-weight: 500;
}
.form-input{
  display: flex;
  flex-direction: column;
  margin: 0 30px ;
}
.form-message{
  color: red;
  font-size: 0.6rem;
  font-weight: 400;
  padding-top: 10px;
}
.form-completed{
  display: none;
}
.form-input label {
  font-size: 0.8rem;
  font-weight: 600;
  padding: 10px 0;
}
.form-input input {
  padding: 10px;
  width: 250px;
  height: 30px;
}
 input:hover{
  border-color: #1dbfaf;
}
button{
  border: 0;
  width: 250px;
  height: 50px;
  background-color: #1DBFAF;
  font-size: 1.4rem;
  font-weight: 700;
  display: block;
  align-items: center;
  margin: 20px auto;
  color: white;
  border-radius: 10px;
}
</style>
