<template>
  <div id="myModal" class="modal">
    <!-- Modal content -->
    <div class="modal-content">
      <div class="close-button">
        <span class="close" v-on:click="closeModal">&times;</span>
      </div>

      <div class="add-first-name">
        <label class="label">First name: </label>
        <input type="search" class="search-bar" v-model="firstNameInput" />
      </div>

      <div class="add-last-name">
        <label class="label">Last name: </label>
        <input type="search" class="search-bar" v-model="lastNameInput" />
      </div>

      <div class="add-email">
        <label class="label">Email: </label>
        <input type="search" class="search-bar" v-model="emailInput" />
      </div>

      <div class="add-sex">
        <label class="label">Sex: </label>
        <select class="sex-dropdown" v-model="sexInput">
          <option value="" selected hidden>Choose sex</option>
          <option value="Male">Male</option>
          <option value="Female">Female</option>
          <option value="Seara tarziu">Seara tarziu</option>
        </select>
      </div>

      <div class="add-birthdate">
        <label class="label">Birthdate: </label>
        <input
          type="date"
          name="birthdate"
          placeholder="Select birthdate"
          class="birth-picker"
          v-model="birthdateInput"
        />
      </div>

      <div class="add-button-div">
        <button class="add-button" @click="addMember">
          Add
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      firstNameInput: "",
      lastNameInput: "",
      emailInput: "",
      sexInput: "",
      birthdateInput: new Date(2018, 8, 1),
    };
  },
  methods: {
    closeModal() {
      var modal = document.getElementById("myModal");
      modal.style.display = "none";
    },
    addMember() {
      var unixBirthdate = Math.round(
        new Date(this.birthdateInput).getTime() / 1000
      );
      axios.post(
        "https://localhost:44380/Home/AddMember",
        `firstName=${this.firstNameInput}&lastName=${this.lastNameInput}&email=${this.emailInput}&sex=${this.sexInput}&birthdate=${unixBirthdate}`
      );
    },
  },
};
</script>

<style>
.close-button {
  display: flex;
  justify-content: end;
  background-color: #96d4d4;
}

.label {
  display: flex;
  background-color: #96d4d4;
  width: 20%;
}

.add-first-name {
  display: flex;
  background-color: #96d4d4;
  width: 100%;
  height: 10%;
  align-items: center;
}

.add-last-name {
  display: flex;
  background-color: #96d4d4;
  width: 100%;
  height: 10%;
  align-items: center;
}

.add-email {
  display: flex;
  background-color: #96d4d4;
  height: 10%;
  align-items: center;
}

.add-sex {
  display: flex;
  background-color: #96d4d4;
  height: 10%;
  align-items: center;
}

.search-bar {
  background: white;
  border: black;
  text-align: center;
  border-radius: 30px;
  width: 80%;
  height: 70%;
}

.search-bar:focus {
  outline: none;
}

.sex-dropdown {
  display: flex;
  background-color: #96d4d4;
  border-radius: 30px;
  height: 70%;
}

.add-birthdate {
  display: flex;
  background-color: #96d4d4;
  border-radius: 30px;
  height: 10%;
  align-items: center;
}

.add-birthdate:before {
  border-radius: 30px;
}

.birth-picker {
  display: flex;
  background: transparent;
  height: 70%;
}

.add-button-div {
  display: flex;
  justify-content: center;
  background-color: #96d4d4;
}

.add-button {
  background-color: white;
  margin-left: 1rem;
  margin-top: 1rem;
  width: 4rem;
}

.modal {
  display: none; /* Hidden by default */
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  background-color: rgb(0, 0, 0); /* Fallback color */
  background-color: rgba(0, 0, 0, 0.4); /* Black w/ opacity */
}

/* Modal Content/Box */
.modal-content {
  background-color: #96d4d4;
  margin: 15% auto; /* 15% from the top and centered */
  padding: 20px;
  border: 1px solid #888;
  width: 30%; /* Could be more or less, depending on screen size */
  height: 50%;
  display: flex;
  justify-content: space-evenly;
  flex-direction: column;
  border-radius: 10%;
}

/* The Close Button */
.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
  background-color: #96d4d4;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}
</style>
