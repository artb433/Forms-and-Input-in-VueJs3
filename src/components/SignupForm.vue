<template>
  <form>
    <label>Email:</label>
    <input type="email" required v-model="email">
    <label>Password:</label>
    <input type="password" required v-model="password">
    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

  
      <input type="checkbox" value="newsletter" v-model="names">
      <label>Newsletter</label>


  
      <input type="checkbox" value="promotions" v-model="names">
      <label>Promotions</label>
    

  
      <input type="checkbox" value="none" v-model="names">
      <label>None</label>
    

    <div class="terms">
      <input type="checkbox" required v-model="terms">
      <label>I agree to the <a href="#">terms and conditions</a></label>
    </div>

  </form>
  <p>Email: {{email}}</p>
  <p>Password: {{password}}</p>
  <p>Role: {{role}}</p>
  <p>Terms: {{terms}}</p>
  <p>Names: {{names}}</p>
</template>

<script>
export default {
  name: "SingupForm",
  created() {},
  data() {
    return {
      email: 'enter your email',
      password: '',
      role: '',
      names: [],
      terms: false
    };
  },
  props: {},
  methods: {},
};
</script>

<style scoped>
form {
max-width: 420px;
margin: 30px auto;
background: white ;
text-align: left;
padding: 40px;
border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
  padding-right: 20px;
}
input, select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border:none;
  border-bottom: 1px solid #ddd;
  color: #555;
}

input[type="checkbox"] {
  display: inline-block;
  width: auto;
  margin-right: 10px;
}
</style>