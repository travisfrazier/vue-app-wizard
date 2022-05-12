<template>
    <header class="header">
        <div class="header-container">
            <g-link to="/">
                <g-image class="logo" alt="Ivanti Logo" src="https://static.ivanti.com/sites/marketing/media/images/logos/ivanti-logo-red.svg" width="135" />
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