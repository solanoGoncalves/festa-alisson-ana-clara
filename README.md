<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Lista de Convidados - Festa de Alisson e Ana Clara Pires</title>
  <style>
    /* Reset básico */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    /* Corpo da página */
    body {
      font-family: 'Arial', sans-serif;
      background: linear-gradient(to bottom, #B3D9FF, #F4E1D2); /* Azul claro e marrom suave */
      color: #000; /* Texto em preto */
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    /* Container principal */
    .container {
      text-align: center;
      background: rgba(255, 255, 255, 0.9); /* Fundo branco translúcido */
      border-radius: 15px;
      padding: 40px;
      width: 90%;
      max-width: 500px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    }

    /* Cabeçalho */
    header h1 {
      font-size: 2.5em;
      color: #4A3C3A; /* Cor marrom suave */
      margin-bottom: 10px;
    }

    header p {
      font-size: 1.3em;
      color: #4A3C3A;
      margin-bottom: 30px;
    }

    /* Formulário */
    .form-container h2 {
      font-size: 2em;
      color: #4A3C3A; /* Cor marrom suave */
      margin-bottom: 20px;
    }

    input {
      padding: 12px;
      margin: 10px 0;
      width: 100%;
      max-width: 400px;
      border: 2px solid #A8C9E7; /* Azul claro */
      border-radius: 8px;
      font-size: 1.1em;
      outline: none;
      transition: border-color 0.3s ease;
    }

    input:focus {
      border-color: #5D3F34; /* Marrom mais escuro no foco */
    }

    button {
      padding: 12px 20px;
      background-color: #5D3F34; /* Marrom */
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 1.3em;
      cursor: pointer;
      width: 100%;
      max-width: 400px;
      margin-top: 20px;
      transition: background-color 0.3s ease;
    }

    button:hover {
      background-color: #3C2F2A; /* Marrom mais escuro no hover */
    }

    /* Mensagem de agradecimento */
    .mensagem-confirmacao {
      display: none;
      background-color: #DFF2BF;
      color: #4F8A10;
      font-size: 1.2em;
      padding: 20px;
      border-radius: 8px;
      margin-top: 20px;
    }

    /* Responsividade */
    @media (max-width: 600px) {
      .container {
        padding: 20px;
      }

      header h1 {
        font-size: 2em;
      }

      .form-container h2 {
        font-size: 1.5em;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <header>
      <h1>Festa de Alisson Pires e Ana Clara Pires</h1>
      <p>Confirme sua presença para a festa incrível que vai rolar!</p>
    </header>

    <div class="form-container">
      <h2>Registro de Convidado</h2>
      <form id="registroForm">
        <input type="text" id="nome" placeholder="Digite seu nome" required>
        <input type="email" id="email" placeholder="Digite seu e-mail" required>
        <button type="submit">Registrar</button>
      </form>
      <!-- Mensagem de confirmação -->
      <div class="mensagem-confirmacao" id="mensagemConfirmacao">
        <p>Obrigado por se registrar! Aguardo você no meu aniversário!</p>
      </div>
    </div>
  </div>

  <script>
    document.addEventListener("DOMContentLoaded", () => {
      const registroForm = document.getElementById("registroForm");
      const mensagemConfirmacao = document.getElementById("mensagemConfirmacao");

      // Registro de convidados
      if (registroForm) {
        registroForm.addEventListener("submit", (e) => {
          e.preventDefault();
          const nome = document.getElementById("nome").value.trim();
          const email = document.getElementById("email").value.trim();

          if (nome && email) {
            const convidados = JSON.parse(localStorage.getItem("convidados") || "[]");
            convidados.push({ nome, email });
            localStorage.setItem("convidados", JSON.stringify(convidados));

            // Exibir a mensagem de confirmação
            mensagemConfirmacao.style.display = "block";
            // Esconde o formulário após o registro
            registroForm.style.display = "none";
          }
        });
      }
    });
  </script>
</body>
</html>
