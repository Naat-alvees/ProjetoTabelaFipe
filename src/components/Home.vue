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
             
              <tr><td>Chevrolet</td><td><button class="btn">Ver modelos</button></td></tr>
              <tr><td>Fiat</td><td><button class="btn">Ver modelos</button></td></tr>
              <tr><td>Ford</td><td><button class="btn">Ver modelos</button></td></tr>
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
              <tr><td>Onix</td></tr>
              <tr><td>Prisma</td></tr>

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

  .table{
    border-collapse: collapse;
    width: 100%;
  }
  .table th, tr, td {
    border-top: 1px solid #E3E6F0;
    border-bottom: 1px solid #E3E6F0;
    text-align: start;
    padding: 0.9em 0.6em;
  }

  .table td{
    width: 50%;
  }

  .btn{
    cursor: pointer;
    background-color: transparent;
    border: 0px;
    color: #4E73DF;
    font-size: 0.9em;
  }

  #rodape{
    background-color: #FFF;
    text-align: center;
    font-size: 0.8em;
    padding: 1em;
  }
</style>
