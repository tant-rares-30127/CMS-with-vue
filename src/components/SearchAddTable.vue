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
