<template>
  <section class="pengguna">
    <app-formulir-input
      v-if="sectionShow === 'masuk'"
      v-model="namaPenggunaMasuk"
      nama="masuk"
      label="Nama Pengguna"
      class="margin-bottom"
    >
      <template #aksi="">
        <app-tombol
          nama="masuk"
          label="Masuk"
          class="margin-left"
          @klik="ketikaTombolMasukDiKlik"
        />
      </template>
    </app-formulir-input>
    <app-formulir-input
      v-if="sectionShow === 'daftar'"
      v-model="namaPenggunaDaftar"
      nama="daftar"
      label="Nama Pengguna"
      class="margin-bottom"
    >
      <template #aksi="">
        <app-tombol
          nama="daftar"
          label="Daftar"
          class="margin-left"
          @klik="ketikaTombolDaftarDiKlik"
        />
      </template>
    </app-formulir-input>
    <!-- <app-tombol
      v-if="sectionShow === 'keluar'"
      nama="keluar"
      label="Keluar"
      @klik="ketikaTombolKeluarDiKlik"
    /> -->
  </section>
</template>

<script>
export default {
  props: {
    sectionShow: {
      type: String,
      default: 'masuk'
    }
  },
  data() {
    return {
      namaPenggunaMasuk: 'kurob',
      namaPenggunaDaftar: null
    }
  },
  methods: {
    ketikaTombolMasukDiKlik() {
      this.$store.dispatch('pengguna/masuk', {
        namaPengguna: this.namaPenggunaMasuk
      })
    },
    ketikaTombolDaftarDiKlik() {
      this.$store.dispatch('pengguna/daftar', {
        namaPengguna: this.namaPenggunaDaftar
      })
    },
    ketikaTombolKeluarDiKlik() {
      this.$store.dispatch('pengguna/keluar')
      this.$emit('keluar')
    }
  }
}
</script>