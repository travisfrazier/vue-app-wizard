<template>
  <Layout class="success-page">
    <section>
      <h2>Thanks for your submission</h2>
      <p>Your request is now with the proper team for approval, and your data will be added shortly. If any further information is needed, the team will reach out to you.</p>
    </section>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: 'Success'
  }
}
</script>

<style lang="scss" scoped>
.home-links a {
  margin-right: 1rem;
}
h2 {
  font-size: 54px;
  font-weight: 600;
  margin-bottom: 20px;
}
section {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
}
p {
  text-align: center;
}
</style>
