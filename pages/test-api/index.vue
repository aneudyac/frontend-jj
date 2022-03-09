/* eslint-disable no-console */
/* eslint-disable no-console */
<template>
  <div>
    <h3>Catálogo de Test API</h3>
    <b-btn @click="nueva">NUEVA</b-btn>
     <b-table hover :items="list" :fields="fields">
       <template #cell(actions)="row">
            <div class="d-flex justify-content-center">
                <b-btn  @click="modificar(row)">Modificar</b-btn>
                <b-btn variant="danger" @click="eliminar(row)">Eliminar</b-btn>
            </div>
        </template>

     </b-table>
  </div>
</template>

<script>
export default {
    name: "TestApi",
    async asyncData({ $axios }) {
      const testApis = await $axios.$get('/test-api')
      const { list } = testApis;
      return { list }
    },
    data() {
      return {
         fields: [
          {
            key: 'Codigo',
            sortable: true
          },
          {
            key: 'Nombre',
            sortable: false
          },
          {
            key: 'Edad',
            label: 'Edad de la persona',
            sortable: true,
            // Variant applies to the whole column, including the header and footer
            variant: 'info'
          },
          {
            key: 'actions'
          }
        ],
      }
    },
    methods: {
      nueva() {
        // eslint-disable-next-line no-console
        console.log('HEy')
        this.$router.push({ path: `/test-api/${0}`})
        // this.$router.push({ path: '/pruebas'})
      },
      modificar({ item }) { 
        // eslint-disable-next-line no-console
        console.log({ item })
        this.$router.push({ path: `/test-api/${item.ID}`})

      },
      eliminar(row) { 
        // eslint-disable-next-line no-console
        console.log({ row })
      }
    }
}
</script>

<style>

</style>