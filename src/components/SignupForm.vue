<template>
  <form @submit.prevent="handleSubmit">
    <label>Email:</label>
    <input type="email" required v-model="email">
    <label>Password:</label>
    <input type="password" required v-model="password">
    <div v-if="passwordError" class="error">{{passwordError}}</div>
    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
      <option value="devops">DevOps</option>
      <option value="sysadmin">System Admininstrator</option>
      <option value="networkadmin">Network Admininstrator</option>
      <option value="databaseadmin">Database Admininstrator</option>
      <option value="dataanalyst">Data Analyst</option>
      <option value="cybersecurity">Cybersecurity</option>
      <option value="itsupport">IT Support</option>
      <option value="projectmanager">Project Manager</option>
      <option value="businessanalyst">Business Analyst</option>
      <option value="qa">Quality Assurance</option>
      <option value="sales">Sales</option>
      <option value="marketing">Marketing</option>
      <option value="finance">Finance</option>
      <option value="hr">Human Resources</option>
      <option value="other">Other</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup="addSkill">
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill  }}</span>
    </div>

    <div>
      <input type="checkbox" value="newsletter" v-model="names">
      <label>Newsletter</label>

      <input type="checkbox" value="promotions" v-model="names">
      <label>Promotions</label>
  
      <input type="checkbox" value="none" v-model="names">
      <label>None</label>
    </div>    

    <div class="terms">
      <input type="checkbox" required v-model="terms">
      <label>I agree to the <a href="#">terms and conditions</a></label>
    </div>

    <div class="submit">
      <button>Creat an Account</button>
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
      email: 'enteryouremail@email.com',
      password: '',
      role: '',
      names: [],
      terms: false,
      tempSkill: '',
      skills: [],
      passwordError: '',
    };
  },
  props: {},
  methods: {
    addSkill(e){
      if(e.key === ',' && this.tempSkill){
        if(!this.skills.includes(this.tempSkill)){
        this.skills.push(this.tempSkill);
        }
        this.tempSkill = '';
      }
    },
    deleteSkill(skill){
      this.skills= this.skills.filter((item) => {
        return item !== skill;
      });
    },
    handleSubmit(){
      console.log("form submitted")
      //validate password
      this.passwordError = this.password.length > 5 ? '' : "Password must be at least 6 characters"
      if(!this.passwordError){
        console.log("Email: " + this.email)
        console.log("Password: " + this.password)
        console.log("Role: " + this.role)
        console.log("Skills: " + this.skills)
        console.log("Terms Accepted: " + this.terms)
      }
    }
  },
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
.pill{
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #eee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}
button {
  background: #0b6dff;
  border: 0;
  padding: 10px 20px;
  margin-top:20px;
  color: white;
  border-radius: 20px;
}
.submit{
  text-align: center;
}
.error{
  color: #ff0062;
  margin-top: 10px;
  font-size: 0.8em;
  font-weight: bold;
}
</style>