<template>
  <v-footer
    padless
    app
    color="cyan"
    >
    <v-card
      class="flex"
      flat
      tile
    >

      <v-card-title class="primary">
        <strong class="subheading" style="color: white;">
          SSC0961 - Desenvolvimento Web e Mobile - ICMC - USP
        </strong>

        <v-spacer></v-spacer>

        <v-btn
          href="https://github.com/mrlFranchi/thanos-defesas"
        > <v-avatar size = "30">
          <img
          src="./../assets/github-mark.png"
          size="50"
          alt = "Github logo para o repositório do projeto"/>
          </v-avatar>
          Repositorio do Projeto
        </v-btn>
      </v-card-title>

      <v-card-text class="primary py-2 white--text text-center">
        {{ new Date().getFullYear() }} — <strong>mrlFranchi</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>
