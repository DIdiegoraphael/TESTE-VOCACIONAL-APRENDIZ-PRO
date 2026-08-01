<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Teste Vocacional Aprendiz Pro</title>
  <link href="https://googleapis.com" rel="stylesheet">
  <style>
    /* CSS CLONE DA SUA IMAGEM DE REFERÊNCIA */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
    }
    body {
      background-color: #123a8c; /* Azul Royal idêntico ao print */
      color: #ffffff;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      padding: 40px 20px;
    }
    .wrapper {
      width: 100%;
      max-width: 680px; /* Largura ideal dos cards */
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .icon-top {
      width: 50px;
      height: 50px;
      background-color: #ffffff;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: 20px;
    }
    /* Seta estilizada simulando o ícone do bússola */
    .icon-top::after {
      content: "🧭";
      font-size: 24px;
    }
    .font-arcade {
      font-family: 'Press Start 2P', monospace;
      color: #ffffff;
      text-align: center;
      font-size: 24px;
      line-height: 1.4;
      margin-bottom: 15px;
      letter-spacing: 1px;
    }
    .subtitle {
      text-align: center;
      font-size: 14px;
      color: #eaf3ff;
      margin-bottom: 35px;
      font-weight: 400;
    }
    .screen {
      display: none;
      width: 100%;
    }
    .screen.active {
      display: block;
    }
    /* Estilo exato dos blocos brancos */
    .card-white {
      background-color: #f8fcff;
      color: #0a0a0a;
      border-radius: 16px;
      padding: 24px 30px;
      margin-bottom: 20px;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
    }
    .card-white h2, .card-white h3 {
      font-size: 18px;
      font-weight: 700;
      margin-bottom: 12px;
      color: #0a0a0a;
    }
    .card-white p {
      font-size: 14px;
      line-height: 1.6;
      color: #0a0a0a;
      font-weight: 500;
    }
    .card-white label {
      display: block;
      font-size: 15px;
      font-weight: 600;
      color: #0a0a0a;
      margin-bottom: 10px;
    }
    .card-white input {
      width: 100%;
      background-color: #f8fcff;
      border: 2px solid #e5e7eb;
      border-radius: 12px;
      padding: 12px 16px;
      color: #0a0a0a;
      font-size: 15px;
      outline: none;
      transition: border-color 0.2s;
    }
    .card-white input:focus {
      border-color: #123a8c;
    }
    .input-small {
      width: 100% !important;
      max-width: 250px;
    }
    .hint-text {
      font-size: 12px;
      color: #6b7280;
      margin-top: 4px;
    }
    /* Botão Amarelo Idêntico à imagem */
    .btn-container {
      text-align: center;
      width: 100%;
      margin-top: 10px;
    }
    .btn-yellow {
      background-color: #f4c542;
      color: #0a0a0a;
      border: none;
      border-radius: 12px;
      padding: 12px 36px;
      font-size: 15px;
      font-weight: 700;
      cursor: pointer;
      transition: background-color 0.2s;
      display: inline-block;
    }
    .btn-yellow:hover {
      background-color: #d9a900;
    }
    /* Estilo do Quiz alinhado com o print */
    .quiz-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 14px;
      font-weight: 600;
      color: #eaf3ff;
      margin-bottom: 20px;
    }
    .progress-bg {
      width: 50%;
      background-color: rgba(255, 255, 255, 0.2);
      height: 8px;
      border-radius: 4px;
      overflow: hidden;
    }
    .progress-bar {
      height: 100%;
      background-color: #f4c542;
      width: 2.5%;
      transition: width 0.3s;
    }
    .likert-btn {
      width: 100%;
      background-color: #f8fcff;
      border: 2px solid #e5e7eb;
      border-radius: 12px;
      padding: 14px 20px;
      color: #0a0a0a;
      text-align: left;
      font-size: 15px;
      font-weight: 500;
      cursor: pointer;
      margin-bottom: 12px;
      transition: all 0.2s;
    }
    .likert-btn:hover {
      background-color: #eaf3ff;
      border-color: #123a8c;
    }
    .spinner {
      width: 45px;
      height: 45px;
      border: 4px solid rgba(255,255,255,0.1);
      border-top: 4px solid #f4c542;
      border-radius: 50%;
      margin: 30px auto;
      animation: spin 1s linear infinite;
    }
    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }
  </style>
</head>
<body>

  <div class="wrapper">
    
    <!-- ÍCONE REDONDO SUPERIOR -->
    <div class="icon-top"></div>

    <!-- TÍTULO ARCADE GAMER -->
    <h1 class="font-arcade">TESTE VOCACIONAL<br>APRENDIZ PRO</h1>
    <p class="subtitle">Descubra a sua âncora de carreira e se desenvolva profissionalmente com propósito</p>

    <!-- TELA 1: BOAS-VINDAS (ESTRUTURA EXATA DO SEU PRINT) -->
    <div id="screen-welcome" class="screen active">
      
      <div class="card-white">
        <h2>O que é teste vocacional Aprendiz Pro?</h2>
        <p>O nosso teste vocacional é um teste orientado pelo conceito das Âncoras de Carreira, modelo criado pelo psicólogo organizacional Edgar H. Schein, do MIT. Elas representam os valores, motivações e competências que guiam suas decisões profissionais ao longo da vida. Este teste identifica qual das oito âncoras é dominante no seu perfil, ajudando você a fazer escolhas de carreira mais alinhadas com quem você realmente é.</p>
      </div>

      <div class="card-white" style="border-left: 4px solid #f4c542;">
        <h3>Como responder</h3>
        <p>Não existem respostas certas ou erradas. Responda de forma espontânea, pensando na sua carreira ideal e nos seus valores — não apenas no seu emprego atual. Leve cerca de 10 minutos para completar as 40 questões.</p>
      </div>

      <div class="card-white">
        <div style="margin-bottom: 20px;">
          <label>Nome do respondente (obrigatório)</label>
          <input id="respondent-name" type="text" required>
        </div>
        
        <div>
          <label>Turma (obrigatório)</label>
          <input id="respondent-class" type="text" placeholder="t01" class="input-small" required>
          <div class="hint-text">Exemplo: t01</div>
        </div>
      </div>

      <div class="btn-container">
        <button onclick="startTest()" class="btn-yellow">Iniciar Teste</button>
      </div>
    </div>

    <!-- TELA 2: QUESTIONÁRIO DIRECIONADO -->
    <div id="screen-quiz" class="screen">
      <div class="quiz-header">
        <span id="quiz-progress-text">Questão 1 de 40</span>
        <div class="progress-bg">
          <div id="quiz-progress-bar" class="progress-bar"></div>
        </div>
      </div>

      <div class="card-white" style="min-height: 110px; margin-bottom: 25px;">
        <p id="question-text" style="font-size: 16px; font-weight: 600;"></p>
      </div>

      <div>
        <button class="likert-btn" onclick="selectScore(5)">5 - Concordo Totalmente</button>
        <button class="likert-btn" onclick="selectScore(4)">4 - Concordo Parcialmente</button>
        <button class="likert-btn" onclick="selectScore(3)">3 - Neutro / Não sei</button>
        <button class="likert-btn" onclick="selectScore(2)">2 - Discordo Parcialmente</button>
        <button class="likert-btn" onclick="selectScore(1)">1 - Discordo Totalmente</button>
      </div>
    </div>

    <!-- TELA 3: PROCESSANDO -->
    <div id="screen-loading" class="screen" style="text-align: center;">
      <div class="spinner"></div>
      <p style="font-weight: 500; color: #eaf3ff;">Calculando seu perfil e sincronizando os resultados...</p>
    </div>

    <!-- TELA 4: RESULTADO FINAL -->
    <div id="screen-result" class="screen">
      <div class="card-white" style="text-align: center;">
        <h2 style="font-size: 22px; margin-bottom: 5px; color: #123a8c;">Teste Concluído!</h2>
        <p style="color: #6b7280; margin-bottom: 20px;">Suas respostas foram salvas com sucesso na planilha.</p>
        
        <div style="background-color: #eaf3ff; border-radius: 12px; padding: 20px; display: inline-block; width: 100%;">
          <span style="font-size: 12px; font-weight: 700; color: #123a8c; text-transform: uppercase; letter-spacing: 1px; display: block; margin-bottom: 8px;">Sua Âncora Dominante:</span>
          <div id="result-anchor" style="font-size: 20px; font-weight: 700; color: #123a8c;">Calculando...</div>
        </div>
      </div>
    </div>

  </div>

  <script>
    let userName = "", userClass = "", currentQuestionIndex = 0, userAnswers = [];

    const ancorasNomes = {
      0: "Competência Técnica / Funcional", 1: "Competência Gerencial Geral", 2: "Autonomia / Independência", 
      3: "Segurança / Estabilidade", 4: "Criatividade Empreendedora", 
      5: "Dedicação a uma Causa / Serviço", 6: "Puro Desafio", 7: "Estilo de Vida"
    };

    const questions = [
      { text: "Quero ser extremamente bom na minha área técnica específica.", cat: 0 },
      { text: "Me motiva a ideia de liderar e gerenciar grandes equipes.", cat: 1 },
      { text: "Eu prefiro trabalho livre, definindo meus próprios horários.", cat: 2 },
      { text: "Prefiro um emprego estável e seguro a assumir riscos de mercado.", cat: 3 },
      { text: "Sonho em construir e abrir meu próprio negócio do zero.", cat: 4 },
      { text: "Para mim, é crucial que meu trabalho ajude a sociedade.", cat: 5 },
      { text: "Me sinto motivado quando preciso resolver problemas quase impossíveis.", cat: 6 },
      { text: "Minha carreira deve se ajustar perfeitamente às minhas necessidades familiares.", cat: 7 },
      { text: "Prefiro ser um specialist reconhecido do que um diretor geral.", cat: 0 },
