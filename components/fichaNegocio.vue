<template>
  <v-card
    class="mx-auto ma-1"
    max-width="544"
    outlined
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
</template>

<script>
export default {
  props: ['negocio'],
  data () {
    return {
      nombreNegocio: "prueba 1"
    }
  }
}
</script>

<style>
</style>