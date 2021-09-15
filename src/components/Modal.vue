<template>
  <div id="myModal" class="modal">
    <!-- Modal content -->
    <div class="modal-content">
      <div class="close-button">
        <span class="close">&times;</span>
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
        <button class="add-button" id="addButton">
          Add
        </button>
      </div>
    </div>
  </div>
</template>
