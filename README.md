# Event-Mouse
Exercicio Compartilhado - ProZ Educacao

<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <script src="script.js" defer></script>
  <link rel="stylesheet" href="style.css">
  <title>Carrinho de compras</title>
</head>
<body>
  <h1>Carrinho de compras</h1>
  <h2>Produtos</h2>
  <section id="carrinho">
    <div class="item-carrinho" id="produto-01">
      <div class="capa"></div>
      <h3>Dom Casmurro</h3>
      <h4>Machado de Assis</h4>
      <p>Valor: R$11.66</p>
      <button id="btn-subtrair-produto-01">-</button>
      <input id="quantidade-produto-01" type="number" value="1" min="0">
      <button id="btn-adicionar-produto-01">+</button>
    </div>
  </section>
  <h2>Subtotal</h2>
  <section id="subtotal">
    <p><span id="quantidade-subtotal">0</span></p>
    <p>R$ <span id="valor-subtotal">0</span></p>
  </section>
</body>
</html>
==========================================================================================

* {
  box-sizing: content-box;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  color: darkslategrey;
}

body {
  background-color: honeydew;
}

#carrinho {
  display: flex;
}

.item-carrinho {
  background-color: lightseagreen;
  margin-right: 2rem;
  padding: 1rem 1.5rem;
  width: 300px;
  border-radius: 8px;
}

.capa {
  width: 80px;
  height: 100px;
  background-color: lightgray;
  position: relative;
}

.capa::after {
  content: "Capa";
  position: absolute;
  transform: translate(-50%, -50%);
  top: 50%;
  left: 50%;
}

input {
  width: 40px;
  text-align: center;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

#subtotal {
  font-size: 1.2rem;
}
========================================================================================

let quantidadeSubtotal = document.getElementById("quantidade-subtotal");
let valorSubtotal = document.getElementById("valor-subtotal");

let subtotalInfo = {
  quantidade: 3,
  valor: 25.66,
};

quantidadeSubtotal.innerText = subtotalInfo.quantidade + " itens";
valorSubtotal.innerText = subtotalInfo.valor;


// ----------- Variaveis / Dados ---------- //

let btnAdicionarProduto01 = document.querySelector("#btn-adicionar-produto-01");
let quantidadeProduto01 = document.querySelector("#quantidade-produto-01");
let btnRemoverProduto01 = document.querySelector("#btn-subtrair-produto-01");

// -------- FUNÇÕES  --------- ///
function atualizarSubtotal() {
  quantidadeSubtotal.innerText = (subtotalInfo.valor * Number(quantidadeProduto01.value)).toFixed(2);
  if (quantidadeProduto01.value == '1') {
    quantidadeSubtotal.innerText = quantidadeProduto01.value + " item";
  } else {
    quantidadeSubtotal.innerText = quantidadeProduto01.value + " itens";
  }
}

function adicionarUm() {
  quantidadeProduto01.value = Number(quantidadeProduto01.value) + 1;
  atualizarSubtotal()
}
console.log(typeof quantidadeProduto01.value);

function removerUm() {
  if (quantidadeProduto01.value != '0') {
    quantidadeProduto01.value = Number(quantidadeProduto01.value) - 1;
  atualizarSubtotal()
  }
}

// ------- EVENTOS ------ ///
btnAdicionarProduto01.addEventListener("click", adicionarUm); 
btnRemoverProduto01.addEventListener("click", removerUm);
