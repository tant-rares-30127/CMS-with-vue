<template>
  <div class="wrapper">
    <Modal></Modal>
    <Title></Title>
    <SearchAddTable></SearchAddTable>
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";
import SearchAddTable from "./components/SearchAddTable.vue";
import Title from "./components/Title.vue";

export default {
  name: "App",
  components: {
    Modal,
    Title,
    SearchAddTable,
  },
};
</script>

<style>
:root {
  --last-name-width: 20%;
  --first-name-width: 35%;
  --email-width: 20%;
  --sex-width: 5%;
  --birthdate-width: 15%;
  --delete-width: 5%;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: #51c4d3;
}

.wrapper {
  display: flex;
  flex-direction: column;
  min-width: 450px;
}
:root {
  --last-name-width: 20%;
  --first-name-width: 35%;
  --email-width: 20%;
  --sex-width: 5%;
  --birthdate-width: 15%;
  --delete-width: 5%;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: #51c4d3;
}

.wrapper {
  display: flex;
  flex-direction: column;
  min-width: 450px;
}
@media (max-width: 1250px) {
  .add-first-name {
    flex-direction: column;
  }
  .add-last-name {
    flex-direction: column;
  }
  .add-email {
    flex-direction: column;
  }
  .add-sex {
    flex-direction: column;
  }
  .add-birthdate {
    flex-direction: column;
  }
  .label {
    width: auto;
  }
  .modal-content {
    width: 50%;
  }
}

@media (max-width: 575px) {
  .add-search {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
}
</style>
