<script>
export default {
    data() {
        return {
            valorDaConta : 0,
            Gorjeta: 15,
            numeroPessoas: 0,
            resultado: "0",
        };
    },
    methods: {
        calcular() {
            const valorDaConta =  this.valorDaConta;
            const Gorjeta = this.Gorjeta;
            const numeroPessoas = this.numeroPessoas;

            if(!numeroPessoas) {
                this.resultado = ""
            }
            let valorDaGorjeta = 0;
            let valorTotal = {};

            valorDaGorjeta = valorDaConta * (Gorjeta / 100);
            valorTotal = (valorDaConta + valorDaGorjeta) / numeroPessoas;

            valorTotal = Math.round(valorTotal * 100) / 100;
            valorTotal = valorTotal.toFixed(2);

            this.resultado = valorTotal

        }
    }
};
</script>

<template>

  <div class="row g-3 align-items-center">
    <h1 class="">Calculadora de Gorjetas</h1>

    <div>
    <div class="col-auto">
      <label class="col-form-label">Preço do serviço:</label>
    </div>
    <div class="col-auto">
      <input
        v-model="valorDaConta"
        id="valorDaConta"
        type="number"
        class="form-control"
        aria-describedby="passwordHelpInline"
      />
    </div>
    </div>

    <div>
    <div class="col-auto">
      <label class="col-form-label">Qualidade do serviço:</label>
    </div>
    <div class="col-auto">
      <select v-model="Gorjeta" id="valorDaGorjeta" class="form-control form-select" aria-label="Default select example">
        <option value="5"> (5%) Péssimo</option>
        <option value="10"> (10%) Ruim</option>
        <option value="15"> (15%) OK</option>
        <option value="20"> (20%) Bom</option>
        <option value="25"> (25%) Mais que bom</option>
        <option value="30"> (30%) Excepcional</option>
      </select>
    </div>
    </div>

    <div>
    <div class="col-auto">
      <label class="col-form-label">Quantas pessoas vão pagar?:</label>
    </div>
    <div class="col-auto">
      <input
        v-model="numeroPessoas"
        type="number"
        id="numeroPessoas"
        @change="calcular()"
        class="form-control"
        aria-describedby="passwordHelpInline"
      />
    </div>
  </div>

  <div class="bg-success text-light rounded p-3 text-center">
    <span id="resultado">{{ resultado }}</span>
  </div>
  </div>
</template>