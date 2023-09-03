<template>
  <v-container>
    <v-row> <!-- class="text-center" >-->
      <v-col cols="3">
        <v-sheet rounded="lg" color="grey lighten-3">
          <v-card>
            <div class="text-center" >
              <v-avatar size="100">
                <img src="https://avatars.githubusercontent.com/u/48134459?v=4" alt="Avatar do Murilo no Github"/>
              </v-avatar>
            </div>
            <v-card-title>Murilo Franchi</v-card-title>
            <v-card-subtitle>nrUSP 9790760</v-card-subtitle>
            <v-card-text>

            </v-card-text>
            <v-card-actions>
              <div class="text-center">
              <v-btn
                text
                style="text-transform: unset !important;"
                outlined
                href="https://github.com/mrlFranchi/"
                target="_blank"
              >
                <v-avatar size="30">
                  <img src="./../assets/github-mark.png" alt="Logo do Github">
                </v-avatar>
                mRlFranchi
              </v-btn>

              <v-btn
                text
                outlined
                href = "https://www.linkedin.com/in/murilo-franchi/"
                target="_blank"
              >
                <img src="./../assets/LI-Logo.png" height = "28" alt = "LinkedIn Logo">
              </v-btn>
              </div>
            </v-card-actions>
          </v-card>
        </v-sheet>
      </v-col>

      <v-col>
        <v-sheet
          min-height="70vh"
          rounded="lg"
        >
         <!--  -->
      </v-sheet>
      </v-col>
    </v-row>
  </v-container>
</template>
