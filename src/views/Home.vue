<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <form v-on:submit.prevent="submit()">
      <h1>Add Information</h1>
      <ul>
        <li class="text-danger" v-for="error in errors" v-bind:key="error">
          {{ error }}
        </li>
      </ul>
      <div class="form-group">
        <label>Color:</label>
        <input type="text" class="form-control" v-model="color">
      </div>
      <div class="form-group">
        <label>Name:</label> 
        <input type="text" class="form-control" v-model="name">
      </div>
      <div class="form-group">
        <label>Style:</label>
        <input type="text" class="form-control" v-model="style">
      </div>
      <div class="form-group">
        <label> Price: </label>
        <input type="text" class="form-control" v-model="price">
      </div>
      <div class="form-group">
        <label>Capacity:</label>
        <input type="text" class="form-control" v-model="capacity">
      </div>
      <input type="submit" class="btn btn-primary" value="Save + Download">
    </form>
  </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios"
export default {
  data: function() {
    return {
      message: "Boat Information File Conversion",
      color: "",
      name: "",
      style: "",
      price: "",
      capacity:"",
      boats: []
    };
  },
  created: function() {
    this.boatsIndex()
  },
  methods: {
    saveBoatInformation() {
      axios.post("/api/").then(response => {
        console.log(response, response.data)
        this.boats = response.data;
      })
    }
  },
};
</script>

//color name style price capacity
