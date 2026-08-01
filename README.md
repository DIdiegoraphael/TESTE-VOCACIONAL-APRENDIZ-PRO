<link href="https://googleapis.com" rel="stylesheet">
<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: 'Poppins', sans-serif;
  }
  body {
    background-color: #123a8c;
    color: #ffffff;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    padding: 50px 24px;
  }
  .wrapper {
    width: 100%;
    max-width: 820px; /* Caixas significativamente mais largas */
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .icon-top {
    width: 65px;
    height: 65px;
    background-color: #ffffff;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 25px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.15);
  }
  .icon-top::after {
    content: "🧭";
    font-size: 32px;
  }
  .font-arcade {
    font-family: 'Press Start 2P', monospace;
    color: #ffffff;
    text-align: center;
    font-size: 36px; /* Título muito maior e visível */
    line-height: 1.5;
    margin-bottom: 20px;
    letter-spacing: 2px;
    width: 100%;
  }
  .subtitle {
    text-align: center;
    font-size: 18px; /* Texto auxiliar maior */
    color: #eaf3ff;
    margin-bottom: 45px;
    font-weight: 400;
    max-width: 650px;
    line-height: 1.4;
  }
  .screen {
    display: none;
    width: 100%;
  }
  .screen.active {
    display: block;
  }
  .card-white {
    background-color: #f8fcff;
    color: #0a0a0a;
    border-radius: 20px;
    padding: 35px 40px; /* Mais espaçamento interno */
    margin-bottom: 25px;
    box-shadow: 0 6px 16px rgba(0, 0, 0, 0.12);
  }
  .card-white h2, .card-white h3 {
    font-size: 24px; /* Títulos internos maiores */
    font-weight: 700;
    margin-bottom: 16px;
    color: #0a0a0a;
  }
  .card-white p {
    font-size: 17px; /* Texto de leitura maior e nítido */
    line-height: 1.7;
    color: #1a1a1a;
    font-weight: 400;
  }
  .card-white label {
    display: block;
    font-size: 18px; /* Labels dos campos maiores */
    font-weight: 600;
    color: #0a0a0a;
    margin-bottom: 12px;
  }
  .card-white input {
    width: 100%;
    background-color: #f8fcff;
    border: 2px solid #d1d5db;
    border-radius: 14px;
    padding: 14px 18px;
    color: #0a0a0a;
    font-size: 18px; /* Texto digitado maior */
    outline: none;
    transition: border-color 0.2s;
  }
  .card-white input:focus {
    border-color: #123a8c;
  }
  .input-small {
    width: 100% !important;
    max-width: 300px;
  }
  .hint-text {
    font-size: 14px;
    color: #6b7280;
    margin-top: 6px;
  }
  .btn-container {
    text-align: center;
    width: 100%;
    margin-top: 15px;
  }
  .btn-yellow {
    background-color: #f4c542;
    color: #0a0a0a;
    border: none;
    border-radius: 14px;
    padding: 16px 50px;
    font-size: 18px; /* Botão maior */
    font-weight: 700;
    cursor: pointer;
    transition: all 0.2s;
    display: inline-block;
    box-shadow: 0 4px 12px rgba(244,197,66,0.3);
  }
  .btn-yellow:hover {
    background-color: #d9a900;
    transform: translateY(-1px);
  }
  .quiz-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 18px;
    font-weight: 600;
    color: #eaf3ff;
    margin-bottom: 25px;
  }
  .progress-bg {
    width: 50%;
    background-color: rgba(255, 255, 255, 0.2);
    height: 10px;
    border-radius: 5px;
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
    border-radius: 14px;
    padding: 18px 24px;
    color: #0a0a0a;
    text-align: left;
    font-size: 18px; /* Opções do quiz maiores */
    font-weight: 500;
    cursor: pointer;
    margin-bottom: 14px;
    transition: all 0.2s;
  }
  .likert-btn:hover {
    background-color: #eaf3ff;
    border-color: #123a8c;
  }
  .spinner {
    width: 55px;
    height: 55px;
    border: 5px solid rgba(255,255,255,0.1);
    border-top: 5px solid #f4c542;
    border-radius: 50%;
    margin: 40px auto;
    animation: spin 1s linear infinite;
  }
  @keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }
</style>

<div class="wrapper">
  <div class="icon-top"></div>

  <h1 class="font-arcade">TESTE VOCACIONAL<br>APRENDIZ PRO</h1>
  <p class="subtitle">Descubra a sua âncora de carreira e se desenvolva profissionalmente com propósito</p>

  <!-- TELA 1: BOAS-VINDAS -->
  <div id="screen-welcome" class="screen active">
    <div class="card-white">
      <h2>O que é teste vocacional Aprendiz Pro?</h2>
      <p>O nosso teste vocacional é um teste orientado pelo conceito das Âncoras de Carreira, modelo criado pelo psicólogo organizacional Edgar H. Schein, do MIT. Elas representam os valores, motivações e competências que guiam suas decisões profissionais ao longo da vida. Este teste identifica qual das oito âncoras é dominante no seu perfil, ajudando você a fazer escolhas de carreira mais alinhadas com quem você realmente é.</p>
    </div>

    <div class="card-white" style="border-left: 5px solid #f4c542;">
      <h3>Como responder</h3>
      <p>Não existem respostas certas ou erradas. Responda de forma espontânea, pensando na sua carreira ideal e nos seus valores — não apenas no seu emprego atual. Leve cerca de 10 minutos para completar as 40 questões.</p>
    </div>

    <div class="card-white">
      <div style="margin-bottom: 24px;">
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

    <div class="card-white" style="min-height: 130px; margin-bottom: 30px;">
      <p id="question-text" style="font-size: 20px; font-weight: 600;"></p>
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
    <p style="font-weight: 500; color: #eaf3ff; font-size: 18px;">Calculando seu perfil e sincronizando os resultados...</p>
  </div>

  <!-- TELA 4: RESULTADO FINAL -->
  <div id="screen-result" class="screen">
    <div class="card-white" style="text-align: center;">
      <h2 style="font-size: 28px; margin-bottom: 10px; color: #123a8c;">Teste Concluído!</h2>
      <p style="color: #6b7280; margin-bottom: 25px; font-size: 16px;">Suas respostas foram salvas com sucesso na planilha.</p>
      
      <div style="background-color: #eaf3ff; border-radius: 16px; padding: 25px; display: inline-block; width: 100%;">
        <span style="font-size: 14px; font-weight: 700; color: #123a8c; text-transform: uppercase; letter-spacing: 1px; display: block; margin-bottom: 10px;">Sua Âncora Dominante:</span>
        <div id="result-anchor" style="font-size: 24px; font-weight: 700; color: #123a8c;">Calculando...</div>
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
    { text: "Prefiro ser um especialista reconhecido do que um diretor geral.", cat: 0 },
    { text: "Gosto de tomar decisões de alto impacto que influenciam a empresa inteira.", cat: 1 },
    { text: "Regras corporativas rígidas e uniformes me incomodam muito.", cat: 2 },
    { text: "Dou muito valor a benefícios de longo prazo and estabilidade.", cat: 3 },
    { text: "Quero criar produtos ou serviços que tenham a minha identidade.", cat: 4 },
    { text: "Não trabalharia em uma instituição que vai contra meus princípios morais.", cat: 5 },
    { text: "Fico entediado com facilidade se as tarefas forem rotineiras.", cat: 6 },
