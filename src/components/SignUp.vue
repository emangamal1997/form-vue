<template lang="html">
  <form class="" action="index.html" method="post" @submit.prevent="submitForm">
    <label for="">Email:</label>
    <input type="email" required v-model="email" />
    <label for="">password:</label>
    <input type="password" required v-model="password" />
    <div class="error" v-if="passwordValidate">{{ passwordValidate }}</div>
    <label for="">Role</label>
    <select v-model="role">
      <option value="back-end">back-end developer</option>
      <option value="front-end">front-end developer</option>
    </select>
    <div class="">
      <input type="checkbox" v-model="terms" />
      <label>I accept terms and conditions</label>
    </div>
    <div>
      <input type="checkbox" v-model="names" value="mareo" />
      <label>mareo</label>
    </div>
    <div>
      <input type="checkbox" v-model="names" value="mark" />
      <label>mark</label>
    </div>
    <div>
      <input type="checkbox" v-model="names" value="emma" />
      <label>emma</label>
    </div>
    <label>skills</label>
    <input type="text" v-model="tempSkills" @keyup.alt="addSkill" />
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="delet(skill)"> {{ skill }}</span>
    </div>
    <p>{{ email }}</p>
    <div class="submit">
      <button type="submit" name="button">submit</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: "ee",
      password: "123",
      role: "",
      terms: "true",
      names: [],
      tempSkills: "",
      skills: [],
      passwordValidate: "",
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkills) {
        if (!this.skills.includes(this.tempSkills)) {
          this.skills.push(this.tempSkills);
          this.tempSkills = "";
        }
      }
    },
    delet(skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item;
      });
    },
    submitForm() {
      this.passwordValidate =
        this.password.length > 5
          ? " "
          : "the password must be longer than 5 char";
    },
  },
};
</script>

<style lang="css" scoped>
form {
  max-width: 420px;
  padding: 40px;
  text-align: left;
  border-radius: 20px;
  margin: 30px auto;
  background-color: white;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
.pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background-color: #eee;
  border-radius: 20px;
  cursor: pointer;
}
.submit {
  text-align: center;
}
button {
  height: 40px;
  color: #3d3636;
  font-size: 15px;
  border-radius: 10px;
  padding: 10px 20px;
  text-align: center;
  margin-top: 20px;
  background-color: #ddd;
  border: none;
}
.error {
  margin-top: 10px;
  font-size: 0.8em;
  font-weight: bold;
  color: #ff0062;
}
</style>
