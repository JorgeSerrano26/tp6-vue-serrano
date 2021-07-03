<template>
  <section class="src-components-datos">
    <div v-if="data.length">
      <table class="table">
        <thead>
          <tr class="table-primary">
            <th class="table-primary" scope="col">Nombre</th>
            <th class="table-primary" scope="col">Edad</th>
            <th class="table-primary" scope="col">Mail</th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="(object, index) in data"
            :key="index"
            class="table-darprimaryk"
          >
            <td class="table-primary">{{ object.nombre }}</td>
            <td class="table-primary">{{ object.edad }}</td>
            <td class="table-primary">{{ object.email }}</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div v-else class="alert alert-warning" role="alert">
      No data
    </div>
  </section>
</template>

<script lang="js">
  export default  {
    name: 'src-components-datos',
    props: [],
    mounted () {
      this.getDataAsync()
    },
    data () {
      return {
        url: '',
        data: []
      }
    },
    methods: {
       getData(){
        this.axios(this.url)
        .then(({data}) => {
          this.data = data
        })
        .catch(error => console.error(error))
      },
       async getDataAsync() {
          this.axios(this.url).then(({data}) => {
            this.data = data;
          })
          .catch((error) => console.error(error))
      }
    },
}
</script>