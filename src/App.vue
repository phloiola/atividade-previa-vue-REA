<template>
  <div>
    {{ msg }}
    <p>
      <label>
        Operador 1
        <input type="number" v-on:input="runOperation()" v-model="operador1" />
      </label>
    </p>

    <p>
      <label>
        Operador 2
        <input type="number" v-on:input="runOperation()" v-model="operador2" />
      </label>
    </p>

    <div>
      <p>
        <label>
          <input
            name="group1"
            type="radio"
            checked
            v-on:input="setOperacao($event.target.value)"
            value="1"
          />
          <span>Somar</span>
        </label>
      </p>
      <p>
        <label>
          <input
            name="group1"
            type="radio"
            v-on:input="setOperacao($event.target.value)"
            value="2"
          />
          <span>Subtrair</span>
        </label>
      </p>
      <p>
        <label>
          <input
            class="with-gap"
            name="group1"
            type="radio"
            v-on:input="setOperacao($event.target.value)"
            value="3"
          />
          <span>Multiplicar</span>
        </label>
      </p>
      <p>
        <label>
          <input
            class="with-gap"
            name="group1"
            type="radio"
            v-on:input="setOperacao($event.target.value)"
            value="4"
          />
          <span>Dividir</span>
        </label>
      </p>
    </div>

    <p v-if="!!result || result === 0">Resultado {{ result }}</p>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      msg: "Calculadora",
      operador1: null,
      operador2: null,
      operacao: "1",
      result: null,
    };
  },
  methods: {
    runOperation: function () {
      if (!this.operador1 || !this.operador2) {
        this.result = null;
        return;
      }
      switch (this.operacao) {
        case "1": // Soma
          this.result = this.operador1 - -this.operador2;
          break;
        case "2": // Subtrai
          this.result = this.operador1 - this.operador2;
          break;
        case "3": // Multiplica
          this.result = this.operador1 * this.operador2;
          break;
        case "4": // Divide
          this.result = this.operador1 / this.operador2;
          break;
        default:
          break;
      }
    },
    setOperacao: function (operacao) {
      this.operacao = operacao;
      this.runOperation();
    },
  },
};
</script>

<style>
body {
  margin: 20px;
}
</style>
