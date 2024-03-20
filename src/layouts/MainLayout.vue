<template>
  <q-layout view="hHh Lpr fFf">
    <q-header elevated class="bg-white">
      <q-toolbar class="text-black">
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title> LIGHT NOVEL </q-toolbar-title>

        <q-input
          v-model="model"
          class="my-3"
          rounded
          outlined
          placeholder="Enter to search"
        >
          <template #append>
            <i-material-symbols-search class="size-1.25em" />
          </template>
        </q-input>

        <q-btn round unelevated class="text-black">
          <i-circum-menu-kebab class="size-1.5em" />
        </q-btn>
        <q-avatar class="size-1.45em">
          <q-img
            src="https://static.cdnno.com/user/7b6ca64c0381d9743781acfc797c8ba6/200.jpg?1642616770"
          />
          <q-menu
            transition-show="scale"
            transition-hide="scale"
            anchor="top start"
            self="top right"
            class="m-0"
          >
            <q-list class="w-250px">
              <q-item clickable :to="'/user'">
                <q-avatar class="mr-1 size-1em">
                  <q-img
                    src="https://static.cdnno.com/user/7b6ca64c0381d9743781acfc797c8ba6/200.jpg?1642616770"
                  />
                </q-avatar>
                <q-item-section class="text-black">
                  <q-item-label class="text-bold text-16px text-orange-400"
                    >Đào Xuân Đông</q-item-label
                  >
                  <q-item-label>@Daoxuandong</q-item-label>
                  <q-item-label class="text-body">
                    View your details
                  </q-item-label>
                </q-item-section>
              </q-item>
              <q-separator />

              <q-item clickable v-ripple>
                <q-avatar>
                  <q-icon class="size-1.25em"><i-ri-google-fill /></q-icon>
                </q-avatar>

                <q-item-section>
                  <q-item-label lines="1">Google Account</q-item-label>
                </q-item-section>
              </q-item>

              <q-item clickable v-ripple :to="'/sign-in'">
                <q-avatar>
                  <q-icon class="size-1.25em"
                    ><i-material-symbols-light-switch-account-outline
                  /></q-icon>
                </q-avatar>

                <q-item-section>
                  <q-item-label lines="1">Switch Account</q-item-label>
                </q-item-section>

                <q-item-section side>
                  <q-icon><i-mingcute-right-line /></q-icon>
                </q-item-section>
              </q-item>

              <q-item clickable v-ripple>
                <q-avatar>
                  <q-icon class="size-1.25em"><i-uit-signout /></q-icon>
                </q-avatar>

                <q-item-section>
                  <q-item-label lines="1">Sign out</q-item-label>
                </q-item-section>
              </q-item>
              <q-separator />
              <q-item clickable v-ripple :to="'/user/settings'">
                <q-avatar>
                  <q-icon class="size-1.25em"
                    ><i-fluent-settings-20-regular
                  /></q-icon>
                </q-avatar>
                <q-item-section> Settings </q-item-section>
              </q-item>
              <q-separator />
              <q-item clickable>
                <q-avatar>
                  <q-icon class="size-1.25em"
                    ><i-material-symbols-light-help-outline
                  /></q-icon>
                </q-avatar>
                <q-item-section>
                  <q-item-label lines="1"> Help</q-item-label>
                </q-item-section>
              </q-item>
              <q-item clickable>
                <q-avatar>
                  <q-icon class="size-1.25em"
                    ><i-material-symbols-light-feedback-outline
                  /></q-icon>
                </q-avatar>
                <q-item-section>Send feedback</q-item-section>
              </q-item>
            </q-list>
          </q-menu>
        </q-avatar>
        <RouterLink :to="'/sign-in'">
          <q-btn text unelevated rounded class="text-black" no-caps>
            Sign In
          </q-btn>
        </RouterLink>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      :width="200"
      show-if-above
      q-mini-drawer-hide
      bordered
    >
      <q-list item="item">
        <q-item
          v-for="{ name, icon, to } in items"
          :key="name"
          clickable
          v-ripple
          :to="to"
        >
          <q-item-section avatar side>
            <Component :is="icon" class="size-1.5em" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ name }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>

      <q-separator />

      <q-list item="item">
        <q-item
          v-for="{ name, icon, to } in itemSupport"
          :key="name"
          clickable
          v-ripple
          :to="to"
        >
          <q-item-section avatar side>
            <Component :is="icon" class="size-1.5em" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ name }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script lang="ts" setup>
import IconRank from "~icons/ant-design/database-filled"
import IconHome from "~icons/ant-design/home-filled"
import IconHelp from "~icons/ant-design/question-circle-filled"
import IconSetting from "~icons/ant-design/setting-filled"
import IconNew from "~icons/eos-icons/compass"
import IconUser from "~icons/mdi/user"
const leftDrawerOpen = ref(false)

const model = ref("")

const items = [
  {
    name: "Home",
    icon: IconHome,
    to: "/"
  },
  {
    name: "News",
    icon: IconNew,
    to: "/news"
  },
  {
    name: "Ranks",
    icon: IconRank,
    to: "/rank"
  }
]
const itemSupport = [
  { name: "Account", icon: IconUser, to: "/user" },
  {
    name: "Settings",
    icon: IconSetting,
    to: "/setting"
  },
  {
    name: "Helps",
    icon: IconHelp,
    to: "/help"
  }
]
</script>
