<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <div class="text-center">
        <v-carousel
          hide-delimiters
          cycle
          height="350"
        >
          <v-carousel-item
            v-for="(item, i) in items"
            :key="i"
            {{ item }}
          >
            <v-sheet height="100%">
              <v-row
                class="fill-height"
                align="center"
                justify="center"
              >
                <div class="display-3">{{ item }}</div>
              </v-row>
            </v-sheet>
          </v-carousel-item>
        </v-carousel>
      </div>
      <v-card>
        <v-card-title class="title">Que buscamos hoy?
        </v-card-title>
        <v-card-text>
          <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quaerat aspernatur at vitae quas, ex et, eius ipsum doloribus voluptatibus veniam sint error ducimus omnis. Consequuntur error possimus nihil dolores ut?</p>
          <v-form>
            <v-container>
              <v-row>
                <v-col
                  cols="12"
                  sm="6"
                >
                  <v-text-field
                    label="Buscar"
                    outlined
                  >
                  </v-text-field>
                </v-col>
              </v-row>
            </v-container>
          </v-form>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            to="/inspire"
          >
            Continue
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
import Logo from "~/components/Logo.vue";
import VuetifyLogo from "~/components/VuetifyLogo.vue";

export default {
  components: {
    Logo,
    VuetifyLogo
  },
  data () {
    return {
      items: ["Negocio 1", "Negocio 2", "Negocio 3", "Negocio 4"]
    };
  }
};
</script>
