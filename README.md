<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Projeto</title>

  <!-- Importação da fonte Space Grotesk no local correto (<head>) -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;600;700&display=swap" rel="stylesheet">

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Space Grotesk', sans-serif;
    }

    body {
      background-color: #0b1528;
      color: #f1f5f9;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      padding: 50px 20px;
    }

    .main-container {
      width: 100%;
      max-width: 800px;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .avatar-badge {
      width: 70px;
      height: 70px;
      background: linear-gradient(135deg, #1e3a8a, #3b82f6);
      border-radius: 22px;
      display: flex;
      align-items: center;
      justify-content: flex-start;
      margin-bottom: 24px;
    }
  </style>
</head>
<body>

  <div class="main-container">
    <div class="avatar-badge">
      <!-- Seu conteúdo aqui -->
    </div>
  </div>

</body>
</html>
