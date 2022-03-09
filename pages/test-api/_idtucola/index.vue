<template>
  <div>
      <h2>{{ item.ID ? 'Editando test api' : 'Nueva test api' }}</h2>
      <b-container fluid>
        <b-row>
            <b-col>
                <b-form-group
                    id="fieldset-codigo"
                    label="Código"
                    label-for="input-codigo"
                >
                    <b-form-input id="input-codigo" v-model="item.Codigo" trim></b-form-input>
                </b-form-group>
            </b-col>
            <b-col>
                <b-form-group 
                    id="fieldset-nombre"
                    label="Nombre"
                    label-for="input-nombre">
                    <b-form-input id="input-nombre" v-model="item.Nombre" trim></b-form-input>
                </b-form-group>
            </b-col>
            <b-col>
                <b-form-group 
                    id="fieldset-edad"
                    label="Edad"
                    label-for="input-edad">
                    <b-form-input id="input-edad" v-model.number="item.Edad"></b-form-input>
                </b-form-group>
            </b-col>
        </b-row>
        <b-row>
            <b-col style="display:flex; justify-content: flex-end;">
                <b-btn variant="primary" @click="guardar">
                    Guardar
                </b-btn>
                <b-btn variant="info" @click="cancelar">
                    Cancelar
                </b-btn>
            </b-col>
        </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
    name: "TestApiUpdate",
     async asyncData({ $axios, params }) {

        let item = {
            ID: null,
            Codigo: null,
            Nombre: null,
            Edad: 0
        }

        if (params.idtucola === '0') return { item }

      const response = await $axios.$get('/test-api/'+params.idtucola)
      item = response.item;
      return { item }
    },
    data() {
        return {}
    },
    computed: {
        Id() {
            // eslint-disable-next-line no-console
            console.log(this.$route.params)
            return this.$route.params.idtucola
        }
    },
    methods: {
        async guardar() {
            try {
                await this.$axios.$post('/test-api', this.item);
                this.$router.push({ path: '/test-api' })
            } catch (error) {
                
            } 

        },
        cancelar() {
            this.$router.push({ path: '/test-api' })
        }
    }
}
</script>

<style>

</style>