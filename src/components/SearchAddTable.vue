<template>
  <div class="search-add-table">
    <div class="add-search">
      <div class="input-border">
        <input type="search" class="member-search-bar" id="searchBar" />
        <span class="search-icon fa fa-search" id="searchIcon"></span>
      </div>

      <div class="modal-button">
        <button class="open-modal-button" id="myBtn">
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
      </table>
    </div>
  </div>
</template>

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
