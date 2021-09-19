<template>
  <div class="search-add-table">
    <div class="add-search">
      <div class="input-border">
        <input type="search" class="member-search-bar" v-model="searchInput" />
        <span class="search-icon fa fa-search" v-on:click="searchMember"></span>
      </div>

      <div class="modal-button">
        <button class="open-modal-button" v-on:click="openModal">
          Add new member
        </button>
      </div>
    </div>

    <div class="members-table">
      <table id="table">
        <thead class="top-row">
          <tr>
            <th class="first-name">First name</th>
            <th class="last-name">Last name</th>
            <th class="email">Email</th>
            <th class="sex">Sex</th>
            <th class="birthdate">Birthdate</th>
            <th class="delete-cell"></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="input in inputs" :key="input.id">
            <td>{{ input.firstName }}</td>
            <td>{{ input.lastName }}</td>
            <td>{{ input.email }}</td>
            <td>{{ input.sex }}</td>
            <td>{{ RefactorDate(input.birthdate) }}</td>
            <td>
              <span
                class="delete-button fa fa-remove"
                v-on:click="deleteMember(input.id)"
              >
              </span>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      inputs: [],
      searchInput: "",
    };
  },
  methods: {
    openModal() {
      var modal = document.getElementById("myModal");
      modal.style.display = "block";
      window.onclick = function(event) {
        if (event.target == modal) {
          modal.style.display = "none";
        }
      };
    },
    getData() {
      axios
        .get("https://localhost:44380/Home/GetTeam")
        .then((response) => {
          return response.data;
        })
        .catch((error) => {
          console.log(error);
        })
        .then((data) => {
          this.inputs = data;
        });
    },
    deleteMember(id) {
      console.log(id);
      axios.delete(`https://localhost:44380/Home/DeleteMember?id=${id}`);
      location.reload();
    },
    searchMember() {
      axios
        .get(`https://localhost:44380/Home/FindMember?name=${this.searchInput}`)
        .then((response) => {
          return response.data;
        })
        .catch((error) => {
          console.log(error);
        })
        .then((data) => {
          this.inputs = data;
        });
    },
    RefactorDate(unixDate) {
      var date = new Date(unixDate * 1000);
      var year = date.getFullYear();
      var month = date.getMonth() + 1;
      var day = date.getDate();
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
    },
  },
  mounted() {
    this.getData();
  },
};
</script>

<style>
table {
  width: 70rem;
}

table,
th,
td {
  border: 1px solid black;
  border-collapse: collapse;
}

th,
td {
  background-color: #96d4d4;
  text-align: center;
}

.add-search {
  display: flex;
  justify-content: center;
  gap: 37rem;
  padding-top: 2rem;
  padding-left: 1.5rem;
  padding-right: 1.5rem;
  padding-bottom: 0.1rem;
}

.modal-button {
  display: flex;
  justify-content: center;
}

.open-modal-button {
  width: 13rem;
  height: 3rem;
  font-size: 1.5rem;
  font-family: Garamond;
  background-color: #96d4d4;
  border-radius: 30px;
}

.input-border {
  display: flex;
  border: 2px solid;
  border-radius: 30px;
  border-color: black;
  width: 20rem;
  height: 3rem;
}

.member-search-bar {
  width: 25rem;
  height: 80%;
  border: transparent;
  background-color: transparent;
  margin-left: 0.5rem;
  margin-top: 0.2rem;
  font-size: medium;
}

.member-search-bar:focus {
  outline: none;
}

.search-icon {
  background: transparent;
  margin-top: 0.8rem;
  margin-right: 0.5rem;
}

.search-add-table {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.members-table {
  display: flex;
  justify-content: center;
}

.top-row {
  height: 2rem;
}

.bottom-row {
  text-align: center;
}

.last-name {
  width: var(--last-name-width);
}

.first-name {
  width: var(--first-name-width);
}

.email {
  width: var(--email-width);
}

.sex {
  width: var(--sex-width);
}

.birthdate {
  width: var(--birthdate-width);
}

.delete-cell {
  width: var(--delete-width);
}

.delete-button {
  background-color: transparent;
  height: 1.5rem;
  width: 3rem;
  margin-top: 0.5rem;
}
</style>
