<template>
  <nav class="nav flex-column justify-content-between">
    <div>
      <router-link
          exact
          :key="i"
          class="nav-link"
          exact-active-class="active"
          :to="{ name: router.name }"
          v-for="(router, i) in routerLinks"
          >
        <i class="fa" :class="`fa-${router.meta.icon}`"></i>
        {{ router.meta.title }}
      </router-link>

      <hr>

      <layout-new-expense/>
    </div>

    <layout-logout>

    </layout-logout>
    <!-- <a class="nav-link active" href="#">Active</a>
    <a class="nav-link" href="#">Link</a>
    <a class="nav-link" href="#">Link</a>
    <a class="nav-link disabled" href="#">Disabled</a> -->
</nav>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import LayoutLogout from './LayoutLogout'
import LayoutNewExpense from './LayoutNewExpense'

export default {

  components: {
    // eslint-disable-next-line vue/no-unused-components
    LayoutLogout,
    // eslint-disable-next-line vue/no-unused-components
    LayoutNewExpense
  },
  computed: {
    routerLinks () {
      return this.$router.options.routes.filter(r => r.name !== 'login')
    }
  }
}
</script>

<style scoped lang="scss">
.nav {
  margin-left: -15px;
  width: calc(100% + 30px);
  height: calc(100vh - 49px);
  .nav-link {
    color: var(--white);
    transition: .4s;
    &.active {
      color: var(--featured);
      background-color: transparent;
    }
    &:hover {
      color: var(--dark);
      background-color: var(--featured);
    }
  }
}
</style>
