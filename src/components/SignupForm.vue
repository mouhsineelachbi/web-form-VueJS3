<template>
  <form>
      <label>Email : *</label>
      <input type="email" required v-model="email">
      
      <label>Password : *</label>
      <input type="password" required v-model="password">

      <label>Role : </label>
      <select v-model="role">
          <option value="developer">Web Developer</option>
          <option value="designer">Web Designer</option>
      </select>

      <div class="terms">
          <input type="checkbox" v-model="terms" required>
          <label>* Accept terms and conditions</label>
      </div>    
  </form>
  Email : {{ email }} <br>
  Password : {{ password }} <br>
  Role : {{ role }} <br>
  Terms : {{ terms }} <br>

</template>

<script>
export default {
    data () {
        return {
            email: '',
            password: '',
            role: '',
            terms: false,
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

</style>