<template>
  <Modal></Modal>
  <Title></Title>
  <SearchAddTable></SearchAddTable>
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
