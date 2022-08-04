<template>
  <div id="app">

    <h2>calculadora Vuejs + axios</h2>
    <h4><i>api Laravel</i></h4>
    <p><span>{{ result }}</span></p>
    <form>  
      <input type="number" v-model.number="n1" /><br /> <br />
      <input type="number" v-model.number="n2" /> <br /> <br />
      <button v-on:click.prevent="Soma">+</button>
      <button v-on:click.prevent="Sub">-</button>
      <button v-on:click.prevent="Mult">x</button>
      <button v-on:click.prevent="Div">/</button>
    </form>
  </div>
</template>
<script>
import api from './components/services/config'
export default {
  data(){
    return{
        n1:'',
        n2:'',
        result:'',
      }
  },
 methods:{
    Soma(){
      api.get('/soma/'+ parseFloat(this.n1)+'/'+ parseFloat(this.n2)).then((response) => {
        this.result = response.data.result
      });
    },
    Sub(){
      api.get('/subtracao/'+ parseFloat(this.n1)+'/'+ parseFloat(this.n2)).then((response) => {
        this.result = response.data.result
      });
    },
    Mult(){
      api.get('/multiplicacao/'+ parseFloat(this.n1)+'/'+ parseFloat(this.n2)).then((response) => {
        this.result = response.data.result
      });
    },
    Div(){
      api.get('/divisao/'+ parseFloat(this.n1)+'/'+ parseFloat(this.n2)).then((response) => {
        this.result = response.data.result
      });
    }
 }
};
</script>

<style>
#app{
  padding: 1rem;
  background: #3a3;
  border-radius:.5rem;

  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  box-shadow: 0 .1rem .3rem .1rem rgba(0,0,0, .3);
}
#app h2{
  text-align: center;
  font-size: 1rem;
}
#app h4{
  text-align: center;
  font-size: .8rem;
}
#app p{
  height: 50px;
  background: #f0f0f0;
  box-shadow: 0 .1rem .3rem .1rem rgba(0,0,0, .3);
  border-radius:.5rem;

  display:flex;
  justify-content: center;
  align-items: center;

}
#app p span{
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  font-size: 2rem;
}
#app form input{
  width: 200px;
  padding:.5rem;
  outline: none;
  border: transparent;
  user-select: none;

  box-shadow: 0 .1rem .3rem .1rem rgba(0,0,0, .3);
  border-radius:.5rem;
}
#app form button{
  width: 50px;
  padding:.5rem;
  outline: none;
  border: transparent;
  user-select: none;

  box-shadow: 0 .1rem .3rem .1rem rgba(0,0,0, .3);
  border-radius:.5rem;
  margin: 0 2px;
}
</style>
