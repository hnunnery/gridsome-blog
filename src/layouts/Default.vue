<template>
  <v-app>
    <v-toolbar>
      <v-toolbar-title>{{ $static.metaData.siteName }}</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn flat exact :to="{ name: 'home' }">Home</v-btn>
        <v-btn flat :to="{ name: 'about' }">About</v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <slot/>
  </v-app>
</template>

<static-query>
query {
  metaData {
    siteName
  }
}
</static-query>

