<template>
  <v-container class="pa-1">
    <v-row
      dense
      class="d-flex flex-column mb-2"
    >
      <v-col
        cols="12"
        class="pa-1"
      >
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
      </v-col>
      <v-col cols="12">
        <v-card>
          <v-card-title class="title">
            Que buscamos hoy?
          </v-card-title>
          <v-card-text>
            <v-form>
              <v-container fluid>
                <v-row align="center">
                  <v-col
                    cols=12
                    sm=8
                  >
                    <v-text-field
                      label="Busqueda"
                      hide-details
                      single-line
                      name=Busqueda
                      prepend-inner-icon="mdi-school"
                      append-outer-icon="mdi-magnify"
                      type=text
                      @click:append-outer="busqueda"
                    />
                  </v-col>
                  <v-col
                    cols=12
                    sm=4
                  >
                    <v-select
                      v-model="filtro"
                      :items="itemsfiltro"
                      chips
                      label="Filtro"
                      multiple
                    ></v-select>
                  </v-col>
                </v-row>
              </v-container>
              <v-container fluid>
                <v-row align="center">
                  <v-col
                    cols=12
                    sm=8
                  >
                    <v-text-field
                      label="Busqueda"
                      hide-details
                      single-line
                      name=Busqueda
                      prepend-inner-icon="mdi-school-outline"
                      append-outer-icon="mdi-magnify"
                      type=text
                      @click:append-outer="busqueda"
                    />
                  </v-col>
                </v-row>
              </v-container>
            </v-form>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12">
        <v-card
          class="mx-auto ma-1"
          max-width="544"
          outlined
          v-for="negocio in jsonnegocios"
          v-bind:key="negocio"
        >
          <v-list-item three-line>
            <v-list-item-content>
              <v-list-item-subtitle class="subtitle-2 font-weight-bold text'justify">
                {{ negocio.nombreEscuela }}
              </v-list-item-subtitle>
              <v-list-item-subtitle>
                <v-chip
                  v-for="item in negocio.giros"
                  v-bind:key="item"
                  color="primary"
                  class="ma-0"
                  small
                >
                  {{ item }}
                </v-chip>
              </v-list-item-subtitle>
              <v-list-item-subtitle class="caption">
                {{ negocio.ubicacion.direccion[0] }} <br />
                {{ negocio.ubicacion.direccion[1] }}
              </v-list-item-subtitle>
            </v-list-item-content>

            <v-list-item-avatar
              size="150"
              tile
            >
              <v-img
                height="100%"
                v-bind:src="'logos/' + negocio.logo +'.png'"
                contain
              >
              </v-img>
            </v-list-item-avatar>
          </v-list-item>
          <v-card-actions>
            <v-btn
              small
              color="primary"
              v-for="contacto in negocio.contactos"
              v-bind:key="contacto.valor"
              rounded
              class="text-none"
            >
              <v-icon
                left
                v-if="contacto.tipo == 'telefono'"
              >
                mdi-phone
              </v-icon>
              <v-icon
                left
                v-if="contacto.tipo == 'facebook'"
              >
                mdi-facebook-box
              </v-icon>{{contacto.valor}}
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
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
      items: ["Negocio 1", "Negocio 2", "Negocio 3", "Negocio 4"],
      itemsfiltro: ['Guarderias', 'Kinder', 'Primarias', 'Secundarias', 'Preparatorias', 'Cursos'],
      terminoBusqueda: 'Termino de busqueda',
      jsonnegocios: [
        {
          "id": 1,
          "nombreEscuela": "Jardin de Ninos Fernando Montes de Oca",
          "giros": ["maternal", "preescolar"],
          "ubicacion": {
            "direccion": ["Paseo del Bosque Mz 35 Lt 14", "Ojo de Agua, Tecamac, Estado de Mexico"],
            "Cordenadas": {
              "lat": 19.657459,
              "long": -99.027109
            }
          },
          "contactos": [
            { "tipo": "telefono", "valor": "59385516" },
            { "tipo": "facebook", "valor": "montessorifmo" }
          ],
          "logo": "realcampestre"
        },
        {
          "id": 2,
          "nombreEscuela": "Grupo Kipling",
          "giros": ["Maternal", "Preesccolar", "Primaria"],
          "ubicacion": {
            "direccion": ["Paseo de la Herradura mz. 74 lt 15", "Ojo de Agua, Tecamac, Estado de Mexico"],
            "Cordenadas": {
              "lat": 19.673716,
              "long": -99.023713
            }
          },
          "contactos": [
            { "tipo": "telefono", "valor": "593875000" },
            { "tipo": "facebook", "valor": "grupokiplingojodeagua" }
          ],
          "logo": "kiplingprimaria"
        }
      ]
    };
  },
  methods: {
    busqueda () {
      console.log("buscando");
    }
  }
};
</script>
<style>
#pruebas {
  width: 10em;
  height: 10em;
  background-color: grey;
}
</style>