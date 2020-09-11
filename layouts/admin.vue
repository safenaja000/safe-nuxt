<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <v-list dense>
        <v-list-item class="text-decoration-none bg-primary" link to="/admin">
          <v-list-item-action>
            <v-icon>mdi-home</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>
              Home
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item class="text-decoration-none" link to="/admin/lawbegin">
          <v-list-item-action>
            <v-icon>*</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>
              คำร้องขอจัดทำร่างกฏหมาย
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item class="text-decoration-none" link to="/admin/lawapprove">
          <v-list-item-action>
            <v-icon>*</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>ร่างกฏหมาย ทั้งหมด</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item class="text-decoration-none" link to="/admin/addpostformlocal">
          <v-list-item-action>
            <v-icon>*</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>เพิ่มการเข้าด้วยระบบเก่า</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item class="text-decoration-none" link to="/admin/addpost">
          <v-list-item-action>
              <v-icon>*</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>เพิมร่างกฏหมาย</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
      </v-list>
      <template v-slot:append>
        <div class="pa-2">
          <v-btn class="text-decoration-none" block to="/">กลับ</v-btn>
        </div>
      </template>
    </v-navigation-drawer>

    <v-app-bar app color="indigo" dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Admin DashBoard</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
          <v-col class="text-center">
            <Nuxt />
          </v-col>
        </v-row>
      </v-container>
    </v-main>
    <v-footer color="indigo" app>
      <span class="white--text">&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: null,
    }
  },
}
</script>

<style></style>
