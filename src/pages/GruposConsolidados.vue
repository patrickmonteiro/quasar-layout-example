<template>
  <q-page padding>
   <div class="q-pa-md">
      <q-table
        title="Treats"
        :data="data"
        :columns="columns"
        row-key="Codigo"
        dark
        :loading="loading"
        color="amber">
        <template v-slot:body="props">
          <q-tr :props="props">
            <q-td key="Codigo" :props="props">{{ props.row.Codigo }}</q-td>
            <q-td key="Nome" :props="props">{{ props.row.Nome }}</q-td>
            <q-td  key="Ação" auto-width :props="props">
              <q-btn dense color="amber-9" icon="search" @click="detalhes(props.row)" />
            </q-td>
          </q-tr>
        </template>
      </q-table>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'GruposConsolidados',
  data () {
    return {
      url: 'https://olinda.bcb.gov.br/olinda/servico/Informes_ListaTarifaPorValores/versao/v1/odata/GruposConsolidados?$top=100&$format=json',
      loading: true,
      columns: [
        { name: 'Codigo', required: true, label: 'Código', align: 'left', field: 'Codigo', sortable: true },
        { name: 'Nome', align: 'center', label: 'Nome', field: 'Nome', sortable: true },
        { name: 'Ação', align: 'center', label: 'Ação', field: 'codigo', sortable: true }
      ],
      data: []
    }
  },
  mounted () {
    this.getGruposConsolidados()
  },
  methods: {
    getGruposConsolidados () {
      this.$axios.get(this.url)
        .then((suc) => {
          this.data = suc.data.value
          this.loading = false
        })
    },
    detalhes (info) {
      alert(JSON.stringify(info))
    }
  }
}
</script>

<style>
</style>
