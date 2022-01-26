<template>
  <div>
    <Header :headerStyle="headerStyle" />
    <Company />
    <Footer />
  </div>
</template>

<script>
export default {
  data() {
    return {
      headerStyle: "dark",
    };
  },
  mounted() {},
};
</script>

<style lang="scss">
</style>
