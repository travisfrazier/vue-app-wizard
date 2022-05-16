<template>
  <Layout>
    <main>
      <Content />
      <Form />
    </main>
  </Layout>
</template>

<script>
import Form from "~/components/Form.vue";
import Content from "~/components/Content.vue";

export default {
  components: {
    Form,
    Content
  },
  metaInfo: {
    title: "Data Intake Wizard",
  },
};
</script>

<style lang="scss" scoped>
.home-links a {
  margin-right: 1rem;
}
main {
  display: flex;
  gap: 30px;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  padding: 0px 15px;
}
.formulate-input, .formulate-input-element {
  width: 100% !important;
  max-width: none !important;
}
</style>
