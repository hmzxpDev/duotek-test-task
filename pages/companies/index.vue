<template>
  <div>
    <Header :headerStyle="headerStyle" />
    <CompanyList />
    <Footer />
  </div>
</template>

<script>
export default {
  data() {
    return {
      headerStyle: "light",
    };
  },
};
</script>

<style lang="scss">
</style>
