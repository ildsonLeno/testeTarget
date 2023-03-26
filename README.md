<h1 align="center">Teste --- Target Sistemas</h1>
<h2 align="center">Repositório criado com as respostas do teste para vaga Estágio Análise e Desenvolvimento.</h2> 


### 1) Observe o trecho de código abaixo:

  int INDICE = 13, SOMA = 0, K = 0;

  enquanto K < INDICE faça

  {

  K = K + 1;

  SOMA = SOMA + K;

  }

  imprimir(SOMA);



  Ao final do processamento, qual será o valor da variável SOMA?


    RESPOSTA: 91


### 2) Dado a sequência de Fibonacci, onde se inicia por 0 e 1 e o próximo valor sempre será a soma dos 2 valores anteriores (exemplo: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34...), escreva um programa na linguagem que desejar onde, informado um número, ele calcule a sequência de Fibonacci e retorne uma mensagem avisando se o número informado pertence ou não a sequência.

IMPORTANTE:

Esse número pode ser informado através de qualquer entrada de sua preferência ou pode ser previamente definido no código;

    RESPOSTA:

    function fibonacci(limite) {
        -- Aqui declarei os termos da sequência
        let a = 0;
        let b = 1;
        -- Criei uma lista vazia para armazenar os termos da sequência
        let list = [];

        while (a <= limite) {
            list.push(a);
            let c = a + b;
            a = b;
            b = c;
        }
        return lista;
    }

    -- Aqui terá que informar um número inteiro positivo
    let numero = parseInt(prompt('Informe um número: '));
    let sequencia = fibonacci(numero);

    -- Aqui vai ser a verificação se o número informado pertence à sequência de Fibonacci
    if (sequencia.includes(numero)) {
        console.log(`O número ${numero} pertence à sequência de Fibonacci.`);
    } else {
        console.log(`O número ${numero} não pertence à sequência de Fibonacci.`);
    }

    console.log(`A sequência de Fibonacci até ${numero} é: ${sequencia}`);


### 3) Dado um vetor que guarda o valor de faturamento diário de uma distribuidora, faça um programa, na linguagem que desejar, que calcule e retorne:
• O menor valor de faturamento ocorrido em um dia do mês;
• O maior valor de faturamento ocorrido em um dia do mês;
• Número de dias no mês em que o valor de faturamento diário foi superior à média mensal.

IMPORTANTE:
a) Usar o json ou xml disponível como fonte dos dados do faturamento mensal;
b) Podem existir dias sem faturamento, como nos finais de semana e feriados. Estes dias devem ser ignorados no cálculo da média;

    RESPOSTA:
    
      const fs = require('fs');
      const faturamentoDiario = JSON.parse(fs.readFileSync('faturamento.json', 'utf-8'));

      let menorFaturamento = faturamentoDiario[0];
      let maiorFaturamento = faturamentoDiario[0];

      const diasComFaturamento = faturamentoDiario.filter(faturamento => faturamento > 0);
      const mediaMensal = diasComFaturamento.reduce((acc, curr) => acc + curr) / diasComFaturamento.length;

      const diasAcimaDaMedia = faturamentoDiario.filter(faturamento => faturamento > mediaMensal).length;

      faturamentoDiario.forEach(faturamento => {
        if (faturamento < menorFaturamento) {
          menorFaturamento = faturamento;
        }
        if (faturamento > maiorFaturamento) {
          maiorFaturamento = faturamento;
        }
      });

      console.log(`Menor valor de faturamento diário: R$ ${menorFaturamento.toFixed(2)}`);
      console.log(`Maior valor de faturamento diário: R$ ${maiorFaturamento.toFixed(2)}`);
      console.log(`Número de dias com faturamento acima da média mensal: ${diasAcimaDaMedia}`);



### 4) Dado o valor de faturamento mensal de uma distribuidora, detalhado por estado:

SP – R$67.836,43
RJ – R$36.678,66
MG – R$29.229,88
ES – R$27.165,48
Outros – R$19.849,53

Escreva em javascript onde calcule o percentual de representação que cada estado teve dentro do valor total mensal da distribuidora.


     RESPOSTA:

     const faturamentoPorEstado = {
      SP: 67836.43,
      RJ: 36678.66,
      MG: 29229.88,
      ES: 27165.48,
      Outros: 19849.53,
    };

    const somaTotal = Object.values(faturamentoPorEstado).reduce((total, valor) => total + valor);

    const percentuaisPorEstado = {};

    for (let estado in faturamentoPorEstado) {
      const percentual = (faturamentoPorEstado[estado] / somaTotal) * 100;
      percentuaisPorEstado[estado] = percentual.toFixed(2);
    }

    console.log(percentuaisPorEstado);

 

### 5) Escreva um programa que inverta os caracteres de um string.

IMPORTANTE:
a) Essa string pode ser informada através de qualquer entrada de sua preferência ou pode ser previamente definida no código;
b) Evite usar funções prontas, como, por exemplo, reverse;

    RESPOSTA:

    let palavra = "uEatartnoc";

    let palavraInvertida = "";

    for (let i = palavra.length - 1; i >= 0; i--) {
      palavraInvertida += palavra[i];
    }

    console.log(palavraInvertida);

