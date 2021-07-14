<template>
  <section>
    <input type="text" v-model="valor">
    <br>
    <p>{{ valor | codificado }} (codificado)</p>
    <br>
    <p>{{ valor | mayus }} (Mayuscula)</p>
    <br>
    <p>{{ valor | min }} (Minuscula)</p>
    <br>
    <p>{{ valor | mayusMin }} (Mayuscula/Minuscula)</p>
    <br>
    <p>{{ valor | minMayu }} (Minuscula/Mayuscula)</p>
    <br>
    <p>Respuestas: 1:B 2:B 3:C 4:A,B 5:B</p>
  </section>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {  
        valor: ''
    }
  },
  filters : {
      codificado: function(value) {
        let valor = '';
        value.split('').forEach(element => {
          switch (element) {
            case 'a':
              valor = valor + 'u'
              break;
            case 'e':
              valor = valor + 'o'
              break;
            case 'o':
              valor = valor + 'e'
              break;
            case 'u':
              valor = valor + 'a'
              break;
            case 'A':
              valor = valor + 'U'
              break;
            case 'E':
              valor = valor + 'O'
              break;
            case 'O':
              valor = valor + 'E'
              break;
            case 'U':
              valor = valor + 'A'
              break;
            default:
              valor = valor + element;
              break;
          }
        });
        return valor;
      },
      mayus: function(value) {
        return value.toUpperCase();
      },
      min: function(value) {
        return value.toLowerCase();
      },
      mayusMin: function(value) {
        var valor = '';
        var array = value.split('')

        for (let index = 0; index < array.length; index++) {
          if((index%2) == 0){
            valor+=array[index].toUpperCase();
          }else{
           valor+=array[index].toLowerCase();
          }
        }

        return valor;
      },minMayu: function(value) {
        var valor = '';
        var array = value.split('')

        for (let index = 0; index < array.length; index++) {
          if((index%2) != 0){
            valor+=array[index].toUpperCase();
          }else{
           valor+=array[index].toLowerCase();
          }
        }

        return valor; 
      }
  },
  methods: {

  }
}
</script>