<template>
  <div id="myModal" class="modal">
    <!-- Modal content -->
    <div class="modal-content">
      <div class="close-button">
        <span class="close" v-on:click="closeModal">&times;</span>
      </div>

      <div class="add-first-name">
        <label class="label">First name: </label>
        <input type="search" class="search-bar" id="firstNameInput" />
      </div>

      <div class="add-last-name">
        <label class="label">Last name: </label>
        <input type="search" class="search-bar" id="lastNameInput" />
      </div>

      <div class="add-email">
        <label class="label">Email: </label>
        <input type="search" class="search-bar" id="emailInput" />
      </div>

      <div class="add-sex">
        <label class="label">Sex: </label>
        <select class="sex-dropdown" id="sexInput">
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
          id="birthdateInput"
        />
      </div>

      <div class="add-button-div">
        <button class="add-button" v-on:click="getData">
          Add
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

function RefactorDate(day, month, year) {
  var namedMonth;
  if (month == 1) namedMonth = " January ";
  if (month == 2) namedMonth = " February ";
  if (month == 3) namedMonth = " March ";
  if (month == 4) namedMonth = " April ";
  if (month == 5) namedMonth = " May ";
  if (month == 6) namedMonth = " June ";
  if (month == 7) namedMonth = " July ";
  if (month == 8) namedMonth = " August ";
  if (month == 9) namedMonth = " September ";
  if (month == 10) namedMonth = " October ";
  if (month == 11) namedMonth = " November ";
  if (month == 12) namedMonth = " December ";
  return day + namedMonth + year;
}

export default {
  methods: {
    closeModal() {
      var modal = document.getElementById("myModal");
      modal.style.display = "none";
    },
    getData() {
      axios
        .get("https://localhost:44364/Home/GetTeam")
        .then(function(response) {
          return response.data.memberList;
        })
        .catch(function(error) {
          console.log(error);
        })
        .then(function(data) {
          for (var i = 0; i < data.length; i++) {
            console.log(data);
            var lastName = data[i].lastName;
            var firstName = data[i].firstName;
            var email = data[i].email;
            var sex = data[i].sex;
            var unixDate = data[i].birthdate;
            var date = new Date(unixDate * 1000);
            var year = date.getFullYear();
            var month = date.getMonth() + 1;
            var day = date.getDate();
            var table = document.getElementById("table");
            var row = table.insertRow();
            row.className = "bottom-row";
            var cell1 = row.insertCell(0);
            var cell2 = row.insertCell(1);
            var cell3 = row.insertCell(2);
            var cell4 = row.insertCell(3);
            var cell5 = row.insertCell(4);
            var cell6 = row.insertCell(5);
            cell1.innerHTML = firstName;
            cell2.innerHTML = lastName;
            cell3.innerHTML = email;
            cell4.innerHTML = sex;
            cell5.innerHTML = RefactorDate(day, month, year);
            cell6.innerHTML =
              '<span class="delete-button fa fa-remove" id="deleteButton">';
          }
        });
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
