<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Aventura com Voltar</title>
  <style>
    .passo {
      display: none;
    }
    .ativo {
      display: block;
    }
    button {
      margin: 5px;
      padding: 10px;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <!-- PASSO 1 -->
  <div class="passo ativo" id="passo-1">
    <h2>Você está no início da aventura</h2>
    <button data-proximo="2">Avançar</button>
  </div>

  <!-- PASSO 2 -->
  <div class="passo" id="passo-2">
    <h2>Você chegou ao passo 2</h2>
    <button data-proximo="3">Avançar</button>
    <button data-voltar="1" class="btn-voltar">Voltar</button>
  </div>

  <!-- PASSO 3 -->
  <div class="passo" id="passo-3">
    <h2>Você chegou ao passo 3</h2>
    <button data-voltar="2" class="btn-voltar">Voltar</button>
  </div>

  <script>
    const passos = document.querySelectorAll('.passo');

    function mostrarPasso(numero) {
      passos.forEach(passo => passo.classList.remove('ativo'));
      document.getElementById(`passo-${numero}`).classList.add('ativo');
    }

    // BOTÕES DE AVANÇO
    document.querySelectorAll('[data-proximo]').forEach(botao => {
      botao.addEventListener('click', () => {
        const proximo = botao.getAttribute('data-proximo');
        mostrarPasso(proximo);
      });
    });

    // BOTÕES DE VOLTAR
    document.querySelectorAll('[data-voltar]').forEach(botao => {
      botao.addEventListener('click', () => {
        const voltar = botao.getAttribute('data-voltar');
        mostrarPasso(voltar);
      });
    });
  </script>

</body>
</html>
