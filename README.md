<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <title>Organizador de Tarefas</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f5f5f5;
      padding: 40px;
    }

    .container {
      max-width: 400px;
      margin: auto;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    h1 {
      text-align: center;
    }

    input {
      width: 70%;
      padding: 8px;
    }

    button {
      padding: 8px 12px;
      cursor: pointer;
    }

    ul {
      list-style: none;
      padding: 0;
      margin-top: 20px;
    }

    li {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 8px;
      border-bottom: 1px solid #ddd;
      cursor: pointer;
    }

    li.concluida {
      text-decoration: line-through;
      color: #999;
    }

    .remover {
      background: #ff4d4d;
      color: #fff;
      border: none;
      border-radius: 4px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>📋 Organizador de Tarefas</h1>

  </div>

  <script>
    const input = document.querySelector("#tarefaInput");
    const botaoAdicionar = document.querySelector("#adicionarBtn");
    const lista = document.querySelector("#listaTarefas");

    botaoAdicionar.addEventListener("click", () => {
      const textoTarefa = input.value.trim();

      if (textoTarefa === "") return;

      const li = document.createElement("li");
      li.textContent = textoTarefa;

      li.addEventListener("click", () => {
        li.classList.toggle("concluida");
      });

      const botaoRemover = document.createElement("button");
      botaoRemover.textContent = "Remover";
      botaoRemover.classList.add("remover");

      botaoRemover.addEventListener("click", (e) => {
        e.stopPropagation(); 
        lista.removeChild(li); 
      });

      li.appendChild(botaoRemover);
      lista.appendChild(li);

      input.value = "";
      input.focus();
    });
  </script>
</body>
</html>
