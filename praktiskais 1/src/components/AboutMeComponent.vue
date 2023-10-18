<template>
    <AboutMeComponent class="about-me-component">
        <h1>ABOUT ME</h1>
            <h3>Name: {{ user.name }}</h3>
            <h3>Surname: {{ user.surname }}</h3>
            <h3>Student code: {{ user.code }}</h3>
    </AboutMeComponent>
  </template>
  
  <script>
  export default {
    data() {
      return {
        user: {
          name: "Laurenss",
          surname: "Lablaiks",
          code: "IT21046",
        },
      };
    },
  };
  </script>
<style scoped>
h1{
      color:white;
    }
.about-me-component {
  display: block;
}
</style>