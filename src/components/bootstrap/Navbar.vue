<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand href="#">HIMIT PENS X DANA INDONESIA</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>

        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-nav-form>
            <b-form-input
              size="sm"
              class="mr-sm-2"
              placeholder="Search"
            ></b-form-input>
            <b-button size="sm" class="my-2 my-sm-0" type="submit"
              >Search</b-button
            >
          </b-nav-form>

          <b-nav-item-dropdown right>
            <!-- Using 'button-content' slot -->
            <template v-slot:button-content>
              <em>User</em>
            </template>
            <b-dropdown-item @click="klik('daftar')" v-if="!$store.state.pengguna.idPengguna">Daftar</b-dropdown-item>
            <b-dropdown-item @click="klik('masuk')" v-if="!$store.state.pengguna.idPengguna">Masuk</b-dropdown-item>
            <b-dropdown-item @click="klik('keluar')" v-if="$store.state.pengguna.idPengguna">Keluar</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {
   name: 'Navbar',
   methods: {
      klik(val){
         this.$emit('klik', val);
         if (val === 'keluar') {
            this.$store.dispatch('pengguna/keluar')
         }
      },
   }
};
</script>

<style>
</style>