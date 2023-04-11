<template>
  <q-layout view="lHh Lpr lff"> 



      <q-header elevated class="bg-grey-10">
        <q-toolbar>
          <q-toolbar-title>Header</q-toolbar-title>
          <q-btn flat @click="drawer = !drawer" round dense icon="menu" />
        </q-toolbar>
      </q-header>



      <q-drawer
        elevated
        v-model="drawer"
        show-if-above
        :width="200"
        :breakpoint="400"
      >



        <q-scroll-area style="height: calc(100% - 150px); margin-top: 150px; border-right: 1px solid #ddd">
          <q-list padding>



            <q-item clickable v-ripple to="/" active-class="bg-grey-10 text-white" exact>
              <q-item-section avatar>
                <q-icon name="inbox" />
              </q-item-section>

              <q-item-section>
                Inicio
              </q-item-section>
            </q-item>



            <q-item clickable v-ripple to="/about" active-class="bg-grey-10 text-white">
              <q-item-section avatar>
                <q-icon name="ti-user" />
              </q-item-section>

              <q-item-section>
                About
              </q-item-section>
            </q-item>



            <q-item clickable v-ripple to="/list" active-class="bg-grey-10 text-white">
              <q-item-section avatar>
                <q-icon name="ti-notepad" />
              </q-item-section>

              <q-item-section>
                List
              </q-item-section>
            </q-item>

            

          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="./interstate-highway-wallpaper.jpg" style="height: 150px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="./cvpic.jpg">
            </q-avatar>
            <div class="text-weight-bold">Juan Cruz Genovese</div>
          </div>
        </q-img>
      </q-drawer>

      <q-page-container>
        <router-view>
          <h1> En desarrollo...</h1>
        </router-view>
      </q-page-container>
    </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const drawer = ref(false)

    return {
      drawer
    }
  }
}
</script>

<style lang="scss">
.my-menu-link {
  color: white;
  background: #F2C037;
}
  
</style>
