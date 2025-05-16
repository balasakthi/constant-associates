<template>
  <v-navigation-drawer
    class="border-0"
    :class="theme.global.current.value.dark ? '' : 'bg-primary'"
    v-model="menuDrawer"
  >
    <v-list>
      <v-list-item class="py-4">
        <template v-slot:prepend>
          <v-img
            :src="
              theme.global.current.value.dark
                ? '/logo/constant-dark.png'
                : '/logo/constant-light.png'
            "
            width="200"
            alt="Logo of constant"
          ></v-img>
        </template>
      </v-list-item>
    </v-list>
    <v-divider></v-divider>

    <v-list role="menu">
      <template v-for="(item, index) in menuItems" :key="index">
        <v-list-group v-if="item.children" :value="item.title">
          <template v-slot:activator="{ props }">
            <v-list-item
              :color="theme.global.current.value.dark ? 'primary' : ''"
              :aria-controls="`${item.title}-dropdown`"
              v-bind="props"
              :prepend-icon="item.icon"
              :title="item.title"
              rounded="xl"
            ></v-list-item>
          </template>

          <v-list-item
            v-for="(sublink, index) in item.children"
            :color="theme.global.current.value.dark ? 'primary' : ''"
            :id="`${sublink.title}-dropdown`"
            :key="index"
            :to="sublink.to"
            :title="sublink.title"
            rounded="xl"
          >
          </v-list-item>
        </v-list-group>

        <v-list-item
          v-else
          :color="theme.global.current.value.dark ? 'primary' : ''"
          :key="index"
          :to="item.to"
          :prepend-icon="item.icon"
          :title="item.title"
          rounded="xl"
        >
        </v-list-item>
      </template>
    </v-list>
  </v-navigation-drawer>
  <v-app-bar>
    <template v-slot:prepend>
      <v-app-bar-nav-icon
        :icon="menuDrawer ? 'mdi-menu-open' : 'mdi-menu-close'"
        @click="menuDrawer = !menuDrawer"
      ></v-app-bar-nav-icon>
    </template>
    <v-app-bar-title class="text-capitalize">
      Automation Application
    </v-app-bar-title>

    <v-spacer></v-spacer>

    <div class="d-flex ga-6 mr-6" v-if="$vuetify.display.mdAndUp">
      <v-autocomplete
        width="230"
        v-model="selectedClient"
        :items="clients"
        hint="Client"
        density="compact"
        clearable
        variant="underlined"
        persistent-hint
      ></v-autocomplete>

      <v-autocomplete
        width="230"
        v-model="selectedProject"
        :items="projects"
        hint="Project"
        density="compact"
        clearable
        variant="underlined"
        persistent-hint
      ></v-autocomplete>
    </div>

    <template #append>
      <v-dialog max-width="500" v-if="$vuetify.display.smAndDown">
        <template v-slot:activator="{ props: activatorProps }">
          <v-btn
            v-bind="activatorProps"
            size="small"
            variant="text"
            icon="mdi-cog"
            flat
          ></v-btn>
        </template>

        <template v-slot:default="{ isActive }">
          <v-card title="Setting">
            <v-card-text>
              <v-autocomplete
                v-model="selectedClient"
                :items="clients"
                hint="Client"
                density="compact"
                clearable
                variant="underlined"
                persistent-hint
              ></v-autocomplete>

              <v-autocomplete
                v-model="selectedProject"
                :items="projects"
                hint="Project"
                density="compact"
                clearable
                variant="underlined"
                persistent-hint
              ></v-autocomplete>
            </v-card-text>

            <v-card-actions>
              <v-spacer></v-spacer>

              <v-btn text="Close" @click="isActive.value = false"></v-btn>
            </v-card-actions>
          </v-card>
        </template>
      </v-dialog>

      <v-btn size="small" variant="text" flat>
        <v-badge color="error" dot>
          <v-icon size="large">mdi-bell-outline</v-icon>
        </v-badge>
      </v-btn>

      <v-btn
        size="small"
        variant="text"
        :icon="
          theme.global.current.value.dark
            ? 'mdi-white-balance-sunny'
            : 'mdi-moon-waning-crescent'
        "
        flat
        @click="toggleTheme"
      ></v-btn>
      <v-btn class="ms-1" icon>
        <v-avatar
          size="small"
          image="https://cdn.vuetifyjs.com/images/john.png"
        />

        <v-menu activator="parent" origin="top">
          <v-list>
            <v-list-item link title="Update profile" />

            <v-list-item link title="Sign out" />
          </v-list>
        </v-menu>
      </v-btn>
    </template>
  </v-app-bar>
</template>

<script setup>
import { shallowRef, onMounted } from "vue";
import { useTheme } from "vuetify";

const theme = useTheme();

const menuDrawer = shallowRef(null);

const menuItems = [
  {
    title: "Home",
    icon: "mdi-home-outline",
    to: "/",
  },
  {
    title: "Admin",
    icon: "mdi-account-tie-outline",
    children: [
      { title: "Users", to: "/users" },
      { title: "Clients", to: "/clients" },
      {
        title: "Projects",
        to: "/projects",
      },
    ],
  },
  {
    title: "Erratas",
    icon: "mdi-bug-check-outline",
    to: "/erratas",
  },
  {
    title: "Word Document",
    icon: "mdi-file-document-outline",
    children: [
      { title: "Document Settings", to: "/document-settings" },
      { title: "Text Styles", to: "/text-styles" },
      {
        title: "Bullet List Settings",
        to: "/bullet-list-settings",
      },
      {
        title: "Ordered List Settings",
        to: "/ordered-list-settings",
      },
      {
        title: "Table Styles",
        to: "/bullet-list-settings",
      },
      { title: "Download Template", to: "/download-template" },
    ],
  },
];

const clients = [
  "Bluewater Solutions",
  "Acme Corporation",
  "Globex Corporation",
  "Soylent Corp",
  "Umbrella Corporation",
  "Vehement Capital Partners",
];

const projects = [
  "Horford County",
  "Social Circle",
  "Harmonious Haven",
  "Civic Connect",
  "Neighborly Nexus",
  "Harmony Zone",
];

const selectedClient = ref("Bluewater Solutions");
const selectedProject = ref("Horford County");

function toggleTheme() {
  theme.global.name.value = theme.global.current.value.dark ? "light" : "dark";
  localStorage.setItem("theme", theme.global.name.value);
}

onMounted(async () => {
  const savedTheme = localStorage.getItem("theme");
  if (savedTheme) {
    theme.global.name.value = savedTheme;
  }
});
</script>
