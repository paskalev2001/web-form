<template>
  <h1>Sign up page</h1>
  <form @submit.prevent="onSubmit">
    <label>Email:</label>
    <input type="email" v-model="email" required />

    <label>Password:</label>
    <input type="password" v-model="password" required />
    <p v-if="passwordError" class="error">{{ passwordError }}</p>

    <label>Role:</label>
    <select v-model="role">
      <option value="user">User</option>
      <option value="mod">Moderator</option>
      <option value="admin">Admin</option>
    </select>

    <div class="check-group">
      <input v-model="terms" type="checkbox" required />
      <label>Accept Terms & Conditions</label>
    </div>

    <div class="check-group">
      <input type="checkbox" value="news" v-model="additional"/>
      <label>Receive Newsletters in your inbox</label>
    </div>

    <div class="check-group">
      <input type="checkbox" value="offers" v-model="additional"/>
      <label>Promotional Offers</label>
    </div>

    <button class="btn">Create Account</button>

  </form>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      role: 'user',
      terms: false,
      additional: [],
    }
  },
  computed: {
    passwordError() {
      if (this.password.length === 0) {
        return ''
      }
      return this.password.length > 6 ? '' : 'Password is too short.'
    }
  },
  methods: {
    onSubmit() {
      if (!this.passwordError) {
        console.log('email:', this.email)
        console.log('password:', this.password)
        console.log('role:', this.role)
        console.log('terms:', this.terms)
        console.log('additional:', this.additional)
      } else {
        console.error('password field is not valid')
      }
    }
  }
}
</script>

<style scoped>
h1 {
  margin-top: 56px;
  text-align: center;
}

form {
  max-width: 480px;
  margin: 40px auto;
  background: whitesmoke;
  text-align: left;
  padding: 30px;
  border-radius: 5px;
}

label {
  color: #aaa;
  display: inline-block;
  margin: 20px 0 20px;
  font-size: 0.8rem;
  text-transform: uppercase;
  letter-spacing: 2px;
  font-weight: 600;
}

input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #444;
}

.check-group {
  display: grid;
  grid-template-columns: 24px 300px;
  grid-column-gap: 10px;
}

.btn {
	box-shadow: 0px 10px 14px -7px #3e7327;
	background:linear-gradient(to bottom, #77b55a 5%, #72b352 100%);
	background-color:#77b55a;
	border-radius:4px;
	border:1px solid #4b8f29;
	display:inline-block;
	cursor:pointer;
	color:#ffffff;
	font-family:Arial;
	font-size:13px;
	font-weight:bold;
	padding:6px 12px;
	text-decoration:none;
	text-shadow:0px 1px 0px #5b8a3c;
}
.btn:hover {
	background:linear-gradient(to bottom, #72b352 5%, #77b55a 100%);
	background-color:#476f33;
  color: rgb(0, 0, 0);
}
.btn:active {
	position:relative;
	top:1px;
}

.error {
  color: red;
}
</style>