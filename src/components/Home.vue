<template>
  <div>
    <!-- Cabeçalho -->
    <div id="cabecalho">
      <h3>Navita</h3>
    </div> 

    <!-- Conteudo -->
    <div id="conteudo">
      <h2>Veículos</h2>

      <!-- Card Marcas -->
      <div class="card">
        <div class="cabecalho-card">
          <p>Marcas</p> 
        </div>
        <div class="conteudo-card">
          <table class="table">
            <thead>
              <tr>
                <th colspan='2'>Marca</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in marcas" :key="item.codigo">
                <td>{{ item.nome }}</td> 
                <td>
                  <button class="btn" v-bind:class="{ 'active':  codigoAtivo  == item.codigo }" v-on:click="carregaModelos(item.codigo)">Ver modelos</button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>

      <!-- Card Modelos -->
      <div class="card" style="margin-top:25px">
        <div class="cabecalho-card">
          <p>Modelos</p> 
        </div>
        <div class="conteudo-card">
          <table class="table">
            <thead>
              <tr>
                <th colspan='2'>Modelo</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item_modelo in modelos" :key="item_modelo.codigo">
                <td>{{ item_modelo.nome }}</td> 
              </tr>
            </tbody>
          </table>
        </div>
      </div>

      
    </div>

    <!-- Rodapé -->
    <div id="rodape">
      <p>Copyright © Navita 2020</p>
    </div>
  </div>

</template>

<script>
import axios from 'axios'
export default {
  name: 'Home',
  data () {
    return {
      marcas: null,
      modelos: null,
      codigoAtivo: ''
    }
  },
  mounted () {
    axios
      .get('https://parallelum.com.br/fipe/api/v1/carros/marcas')
      .then(response => {
        this.marcas = response.data;
      })
      .catch(error => {
        console.log(error)
      })
  },
  methods: {
    carregaModelos: function (id_marca) {
      console.log(id_marca);
      this.codigoAtivo = id_marca;
      axios
        .get('https://parallelum.com.br/fipe/api/v1/carros/marcas/'+id_marca+'/modelos')
        .then(response => {
          this.modelos = response.data.modelos;
        })
        .catch(error => {
          console.log(error)
        })
      }
  }

}
</script>

<style scoped>
  #cabecalho{
    background-color: #FFF;
    padding: 0em 1.2em;
    padding-top: 0.4em;
    border-bottom: 1px solid #E3E6F0;
  }

  #cabecalho h3{
    color: #1CC88A;
  }

  #conteudo{
    background-color: #F7F8FB;
    padding: 0.4em 1.2em;
  }

  .card{
    background-color: #FFF;
    border-radius: 5px;
    box-shadow: 0 0 1.2em 0.2em rgba(58, 59, 69, .15);
  }

  .card .cabecalho-card{
    background-color: #F8F9FC;
    border-radius: 5px 5px 0px 0px;
    border-bottom: 1px solid #E3E6F0;
    padding: 0.1em 1em;
    color: #4E73DF;
    font-weight: bold;
  }

  .card .conteudo-card{
    padding: 1.5em 1em;
  }

  table {
    display: flex;
    flex-flow: column;
    height: 25em;
    width: 100%;
    border-collapse: collapse;
  }

  table thead {
      flex: 0 0 auto;
      width: calc(100% - 0.9em);
  }

  table tbody {
      flex: 1 1 auto;
      display: block;
      overflow-y: scroll;
  }

  table tbody tr {
      width: 100%;
  }

  table td{
    width: 50%;
  }

  table thead,
  table tbody tr {
      display: table;
      table-layout: fixed;
  }

  table th, tr, td {
    border-top: 1px solid #E3E6F0;
    border-bottom: 1px solid #E3E6F0;
    text-align: start;
    padding: 0.9em 0.6em;
  }

  .btn{
    cursor: pointer;
    background-color: transparent;
    border: 0px;
    color: #4E73DF;
    font-size: 0.9em;
  }

  .active, .btn:hover {
    color: #1CC88A;
  }

  #rodape{
    background-color: #FFF;
    text-align: center;
    font-size: 0.8em;
    padding: 1em;
  }
</style>
