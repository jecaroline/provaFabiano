<template>

  <div>
      <label for="nome"> Nome do Aluno: </label>
      <input type="text" id="nome" v-model="nome" size="30"><br/><br/>
      <label for="nota1"> Nota 1: </label>
      <input type="text" id="nota1" v-model="nota1" size="5"><br/><br/>
      <label for="nota2"> Nota 2: </label>
      <input type="text" id="nota2" v-model="nota2" size="5"><br/><br/>
      <label for="nota3"> Nota 3: </label>
      <input type="text" id="nota3" v-model="nota3" size="5"><br/><br/>

      <button @click="inserir()">Calcular</button>


    <div>
      <table>
        <tr>
          <td>Nome Aluno</td>
          <td>Status</td>
        </tr> 
        <tr v-for="a in alunos" :key="a.alunos" @click ="inserir(a)"> 
          <td>{{ a.nome }}</td>
         <td>{{ a.status }} </td>
        </tr>

      </table>
    </div>   
  </div>
  
</template>

<script>


export default {
  data() {
    return {
      alunos: [
        {
          nome: '',
          nota1: 0,
          nota2: 0,
          nota3: 0,
          media: 0,
          status:''
        }
      ]
    }
  },

  methods:{
    inserir() {
      this.alunos.push(
        {
          nome: this.nome,
          nota1: this.nota1,
          nota2:this.nota2,
          nota3: this.nota3,
          media: this.calculaMedia(),
          status: this.status
          
        },

        this.nome = '',
        this.nota1 = '',
        this.nota2 = '',
        this.nota3 = '',

     ) 
      console.log(this.alunos)
    },

    calculaMedia(){

        this.media =  (this.nota1 + (this.nota2 * 2) + (this.nota3 * 3)) / 6

          if (this.media > 7) {
            this.status = 'Aprovado'
          }
          else {
           this.status = 'Reprovado'
          }
        return this.media
         
    }   
  

  }
}


</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
