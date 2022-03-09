<template>
<div>
   <b-navbar toggleable="lg" type="dark" variant="info">
    <!-- <b-navbar-brand href="/">NavBar</b-navbar-brand> -->
    <NuxtLink class="nav-link" to="/">APP</NuxtLink>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item href="javascript:void(0)">
        </b-nav-item>
        <NuxtLink class="nav-link" to="/test-api">Test api</NuxtLink>
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <b-nav-form>
          <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
          <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
        </b-nav-form>
<!-- 
        <b-nav-item-dropdown right>
          <template #button-content>
            <em>User</em>
          </template>
          <b-dropdown-item href="#">Profile</b-dropdown-item>
          <b-dropdown-item href="#">Sign Out</b-dropdown-item>
        </b-nav-item-dropdown> -->
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
  <nuxt />
</div>
</template>

<script>
export default {
    name: "LayoutDefault"
}
</script>

<style>

</style>