<template>
  <div>
    <form @submit.prevent="submitForm">
      <label for="fname">Firstname:</label>
      <input type="text" name="fname" id="fname" v-model="fname" />
      <label for="lname">Lastname:</label>
      <input type="text" name="lname" id="lname" v-model="lname" />
      <label for="style">Email:</label>
      <input type="email" name="email" id="email" v-model="email" />
      
      <button type="submit">Submit</button>
    </form>
    <table>
      <thead>
        <tr>
          <th>Firstname</th>
          <th>Lastname</th>
          <th>Email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(entry, index) in entries" :key="index">
          <td>{{ entry.fname }}</td>
          <td>{{ entry.lname }}</td>
          <td>{{ entry.email }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      fname: "",
      lname: "",
      email: "",
      entries: [],
    };
  },
  computed: {
    fullname() {
      return this.fname + " " + this.lname+ " " + this.email;
    },
  },
  methods: {
    submitForm() {
      this.entries.push({
        fname: this.fname,
        lname: this.lname,
        email: this.email,
        
        
      });
      this.fname = "";
      this.lname = "";
      this.email = "";
      
    },
  },
};
</script>
<style scoped>
button{
  background:blue;
  color: white;
  margin: 10px;
  width: 5%;
  height: 10%;
  border-radius: 5px;
}
</style>
