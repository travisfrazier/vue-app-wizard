<template>
  <footer>
    <div class="footer-content">
      <g-link to="/">
        <g-image
          class="logo"
          alt="Logo"
          src="https://images.unsplash.com/photo-1542903660-eedba2cda473?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2070&q=80"
          width="135"
        />
      </g-link>
      <div class="menu-item"><a href="" target="_blank"><span>Privacy and Legal</span></a></div>
    </div>
  </footer>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
footer {
  bottom: 0;
  height: auto;
  background: $white;
  width: 100%;
  margin-top: 100px;
}
.logo {
  width: 75px;
}
.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 30px 15px;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}
a {
    color: $gray;
    font-size: 14px;
}
</style>