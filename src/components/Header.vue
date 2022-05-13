<template>
    <header class="header">
        <div class="header-container">
            <g-link to="/">
                <g-image class="logo" alt="Logo" src="https://images.unsplash.com/photo-1542903660-eedba2cda473?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2070&q=80" width="135" />
            </g-link>
        </div>
    </header>
</template>

<script>
    export default {
    }
</script>

<style lang="scss" scoped>
.header {
  position: fixed;
  top: 0;
  display: flex;
  align-items: center;
  height: auto;
  padding: 20px 0px;
  background: $white;
  width: 100%;
  box-shadow: 0 10px 20px -8px rgb(52, 52, 52);
  z-index: 999;
}

.header-container {
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  padding: 0px 15px;
}

.nav__link {
  margin-left: 20px;
}

.logo {
  width: 140px;
}
</style>