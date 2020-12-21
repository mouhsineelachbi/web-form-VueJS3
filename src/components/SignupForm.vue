<template>
  <form @submit.prevent="handleSubmit"> <!-- adding prevent event modifier to prevent refreshing the form after submitting -->
      <label>Email : *</label>
      <input type="email" required v-model="email">
      
      <label>Password : *</label>
      <input type="password" required v-model="password">
      <div v-if="passwordError" class="error">
          {{ passwordError }}
      </div>

      <label>Role : </label>
      <select v-model="role">
          <option value="developer">Web Developer</option>
          <option value="designer">Web Designer</option>
      </select>

      <div>
          <label>Skills : </label>
          <input type="text" v-model="tempSkill" @keyup.alt="addSkills"/>
          <ul>
          <div v-for="skill in skills" :key="skill" class="pill">
              <!-- <li @click="deleteSkill(skill)"> {{ skill }} </li> -->
              <span @click="deleteSkill(skill)">{{ skill }}</span>
          </div>
          </ul>
      </div>

      <div class="terms">
          <input type="checkbox" v-model="terms" required>
          <label>* Accept terms and conditions</label>
      </div>

      <div class="submit">
          <button>Create account</button>
      </div>

      
      <!-- 
          In case of multiple checkboxes
      <div>
          <input type="checkbox" value="muslim" v-model="names">
          <label>Muslim</label>
      </div>

      <div>
          <input type="checkbox" value="christian" v-model="names">
          <label>Christian</label>
      </div>

      <div>
          <input type="checkbox" value="jewish" v-model="names">
          <label>Jewish</label> 
      </div> -->     
  </form>

    <p>Testing</p>
    <p>

  Email : {{ email }} <br>
  Password : {{ password }} <br>
  Role : {{ role }} <br>
  Terms : {{ terms }} <br>
    </p>
</template>

<script>
export default {
    data () {
        return {
            email: '',
            password: '',
            role: '',
            terms: false,
            //names: [],
            tempSkill: '',
            skills: [],
            passwordError: '',
        }
    },
    methods: {
        addSkills (e) {
            if (e.key === ';' && this.tempSkill){
                if(!this.skills.includes(this.tempSkill)){
                    this.skills.push(this.tempSkill);
                }
                this.tempSkill = '';
            }
        },
        deleteSkill (skill) {
            this.skills = this.skills.filter(item => item != skill );
        },
        handleSubmit () {
            //  Password validation using ternary operator
            this.passwordError = this.password.length > 5 ? 
                                '' : 'Password must be at least 6 chars long';
            if ( !this.passwordError )  {
                console.log(`Email : ${this.email}`);
                console.log(`Password : ${this.password}`);
                console.log(`Role : ${this.role}`);
                console.log(`Skills : ${this.skills}`);
                console.log(`Terms accepted : ${this.terms}`);
            }
        }
    }
}
</script>

<style>
    form {
        max-width: 420px;
        margin: 30px auto;
        background: white;
        text-align: left;
        padding: 40px;
        border-radius: 10px;
    }

    label {
        color: #aaa;
        display: inline;
        margin: 25px 0;
        font-size: 0.6em;
        text-transform: uppercase;
        letter-spacing: 1px;
        font-weight: bold;
    }

    input, select {
        margin: 20px auto;
        display: block;
        padding: 10px;
        width: 100%;
        box-sizing: border-box;
        border: none;
        border-bottom: 1px solid #ddd;
        color: #555;
    }

    input[type="checkbox"] {
        display: inline-block;
        width: 16px;
        margin: 0 10px 0;
        position: relative;
        top: 2px
    }

    .pill {
        background: #eee;
        display: inline-block;
        margin: 20px 10px 0 0;
        padding: 6px 12px;
        border-radius: 20px;
        font-size: 12px;
        letter-spacing: 1px;
        font-weight: bold;
        color: #777;
        cursor: pointer;
    }
    
    button {
        background: #0b6dff;
        border: 0px;
        padding: 10px 20px;
        margin-top: 20px;
        color: white;
        border-radius: 20px;
    }

    .submit {
        text-align: center;
    }

    .error {
        color: #ff0062;
        margin-top: 10px;
        margin-bottom: 10px;
        font-size: 0.8em;
        font-weight: bold;
    }
</style>