<template>
  <div class="layout">
    <Header />
    <div class="content-container">
      <slot/>
    </div>
    <Footer />
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
import Header from "~/components/Header.vue";
import Footer from "~/components/Footer.vue";

export default {
  components: {
    Header,
    Footer
  },
  metaInfo: {
    title: "Ivanti",
  },
};
</script>

<style lang="scss">
body {
  font-family: $font-family-inter;
  margin:0;
  padding:0;
  line-height: 1.5;
  background-color: $wild-sand;
  position: relative;
  padding-top: 200px;
}

.layout {
  margin: 0 auto;
  height: 100%;
}

.content-container {
  max-width: 960px;
  margin: 0 auto;
}
</style>
