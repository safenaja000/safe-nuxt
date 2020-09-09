<template>
  <div class="container">
    <div class="container-fluid my-5">
      <div class="row">
        <div class="col-lg-4 ml-auto">
          <v-text-field
            v-model="search"
            append-icon="mdi-magnify"
            label="Search"
            single-line
            hide-details
          ></v-text-field>
        </div>
        <div class="col-lg-12">
          <v-data-table
            :headers="headers"
            class="elevation-1"
            :items="users"
            :search="search"
          >
            <template v-slot:item.edit="{ item }">
              <v-btn color="success" @click="clicked(item.id_card)"
                >Approve</v-btn
              >
            </template>
          </v-data-table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Swal from 'sweetalert2'
export default {
  layout: 'admin',
  async asyncData({ $axios }) {
    const res = await $axios.$get('/member')
    return {
      users: res.data.filter((user) => user.user_status !== 7),
    }
  },
  data() {
    return {
      headers: [
        { text: 'username', value: 'username', align: 'center', width: '1em' },
        { text: 'name', value: 'name', align: 'left', width: '3em' },
        {
          text: 'email',
          value: 'email_address',
          align: 'center',
          width: '3em',
        },
        { text: 'Edit', value: 'edit', align: 'center', width: '2em' },
      ],
      users: [],
      search: '',
    }
  },
  methods: {
    clicked(idCard) {
      Swal.fire({
        title: 'Are you sure?',
        text: "You won't be able to revert this!",
        icon: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#3085d6',
        cancelButtonColor: '#d33',
        confirmButtonText: 'Yes, Approve it!',
      }).then((result) => {
        if (result.value) {
          Swal.fire('Send!', 'Your request Successful', 'success')
          this.approveUser(idCard)
        }
      })
    },
    async approveUser(idCard) {
      const res = await this.$axios.$post(`/member/${idCard}`, {
        user_status: 7,
      })
      if (res.status === 'OK') {
        this.getAllUsers()
      }
    },
    async getAllUsers() {
      const res = await this.$axios.$get('/member')
      this.users = res.data.filter((user) => user.user_status !== 7)
    },
  },
}
</script>

<style></style>
