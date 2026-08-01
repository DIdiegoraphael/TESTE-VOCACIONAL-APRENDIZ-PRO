<link href="https://googleapis.com" rel="stylesheet">

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
    min-height: 110vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    padding: 60px 20px;
    
    /* Força o conteúdo a subir e cobrir fisicamente a barra azul externa */
    margin-top: -120px !important; 
    position: relative;
    z-index: 99999;
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
    justify-content: center;
    margin-bottom: 20px;
    box-shadow: 0 8px 24px rgba(59, 130, 246, 0.25);
  }

  .avatar-badge::after {
    content: "🧭";
    font-size: 34px;
  }

  .tagline {
    text-align: center;
    font-size: 18px;
    color: #94a3b8;
    margin-bottom: 40px;
    max-width: 600px;
    line-height: 1.5;
    font-weight: 400;
  }

  .screen-panel {
    display: none;
    width: 100%;
  }

  .screen-panel.active {
    display: block;
  }

  .content-card {
    background-color: #ffffff;
    color: #0f172a;
    border-radius: 24px;
    padding: 40px;
    margin-bottom: 28px;
    box-shadow: 0 12px 32px rgba(0, 0, 0, 0.2);
  }

  .content-card h2, .content-card h3 {
    font-size: 24px;
    font-weight: 700;
    margin-bottom: 16px;
    color: #0f172a;
  }

  .content-card p {
    font-size: 16px;
    line-height: 1.7;
    color: #334155;
  }

  .input-wrapper {
    margin-bottom: 28px;
  }

  .input-wrapper label {
    display: block;
    font-size: 15px;
    font-weight: 600;
    color: #1e293b;
    margin-bottom: 10px;
  }

  .input-field {
    width: 100%;
    background-color: #f8fafc;
    border: 2px solid #e2e8f0;
    border-radius: 16px;
    padding: 16px 20px;
    color: #0f172a;
    font-size: 16px;
    outline: none;
  }

  .input-field:focus {
    border-color: #3b82f6;
    background-color: #ffffff;
  }

  .size-class {
    max-width: 200px;
    text-transform: uppercase;
  }

  .caption {
    font-size: 13px;
    color: #64748b;
    margin-top: 6px;
  }

  .action-container {
    text-align: center;
    width: 100%;
  }

  .btn-submit {
    background-color: #f4c542;
    color: #0b1528;
    border: none;
    border-radius: 18px;
    padding: 18px 60px;
    font-size: 16px;
    font-weight: 700;
    text-transform: uppercase;
    cursor: pointer;
    box-shadow: 0 6px 20px rgba(244, 197, 66, 0.3);
  }

  .btn-submit:hover {
    background-color: #e0b334;
  }

  .quiz-status {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 15px;
    font-weight: 600;
    color: #94a3b8;
    margin-bottom: 28px;
  }

  .track-bg {
    width: 50%;
    background-color: #1e293b;
    height: 10px;
    border-radius: 6px;
    overflow: hidden;
  }

  .track-fill {
    height: 100%;
    background-color: #f4c542;
    width: 2.5%;
    transition: width 0.3s ease;
  }

  .option-btn {
    width: 100%;
    background-color: #ffffff;
    border: 2px solid #e2e8f0;
    border-radius: 18px;
    padding: 18px 24px;
    color: #0f172a;
    text-align: left;
    font-size: 16px;
    font-weight: 500;
    cursor: pointer;
    margin-bottom: 14px;
  }

  .option-btn:hover {
    border-color: #3b82f6;
    background-color: #f8fafc;
  }

  .loader-spinner {
    width: 60px;
    height: 60px;
    border: 5px solid #1e293b;
    border-top: 5px solid #f4c542;
    border-radius: 50%;
    margin: 50px auto 24px auto;
    animation: turn 1s linear infinite;
  }

  @keyframes turn {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }
</style>

<div class="main-container">
  
  <div class="avatar-badge" style="margin-top: 40px;"></div>

  <p class="tagline">Descubra a sua âncora de carreira e se desenvolva profissionalmente com propósito</p>

  <!-- TELA 1: BOAS-VINDAS -->
  <div id="screen-welcome" class="screen-panel active">
    
    <div class="content-card">
      <!-- Título Corrigido Conforme Solicitado -->
      <h2>O que é o teste vocacional Aprendiz Pro?</h2>
      <p>O nosso teste vocacional é um teste orientado pelo conceito das Âncoras de Carreira, modelo criado pelo psicólogo organizacional Edgar H. Schein, do MIT. Elas representam os valores, motivações e competências que guiam suas decisões profissionais ao longo da vida. Este teste identifica qual das oito âncoras é dominante no seu perfil, ajudando você a fazer escolhas de carreira mais alinhadas com quem você realmente é.</p>
    </div>

    <div class="content-card" style="border-left: 6px solid #f4c542;">
      <h3>Como responder</h3>
      <p>Não existem respostas certas ou erradas. Responda de forma espontânea, thinking na sua carreira ideal e nos seus valores — não apenas no seu emprego atual. Leve cerca de 10 minutos para completar as 40 questões.</p>
    </div>

    <div class="content-card">
      <div class="input-wrapper">
        <label>Nome do respondente (obrigatório)</label>
        <input id="respondent-name" type="text" class="input-field" autocomplete="off">
      </div>
      
      <div class="input-wrapper">
        <label>Turma (obrigatório)</label>
        <input id="respondent-class" type="text" placeholder="t01" class="input-field size-class" autocomplete="off">
        <div class="caption">Exemplo: t01</div>
      </div>
    </div>

    <div class="action-container">
      <button onclick="startTest()" class="btn-submit">Iniciar Teste</button>
    </div>
  </div>

  <!-- TELA 2: QUESTIONÁRIO DIRECIONADO -->
  <div id="screen-quiz" class="screen-panel">
    <div class="quiz-status">
      <span id="quiz-progress-text">Questão 1 de 40</span>
      <div class="track-bg">
        <div id="quiz-progress-bar" class="track-fill"></div>
      </div>
    </div>

    <div class="content-card" style="min-height: 140px; margin-bottom: 35px;">
      <p id="question-text" style="font-size: 18px; font-weight: 600; color: #0f172a;"></p>
    </div>

    <div>
      <button class="option-btn" onclick="selectScore(5)">5 - Concordo Totalmente</button>
      <button class="option-btn" onclick="selectScore(4)">4 - Concordo Parcialmente</button>
      <button class="option-btn" onclick="selectScore(3)">3 - Neutro / Não sei</button>
      <button class="option-btn" onclick="selectScore(2)">2 - Discordo Parcialmente</button>
      <button class="option-btn" onclick="selectScore(1)">1 - Discordo Totalmente</button>
    </div>
  </div>

  <!-- TELA 3: PROCESSANDO -->
  <div id="screen-loading" class="screen-panel" style="text-align: center;">
    <div class="loader-spinner"></div>
    <p style="font-weight: 500; color: #94a3b8; font-size: 18px;">Computando afinidades e salvando perfil...</p>
  </div>

  <!-- TELA 4: RESULTADO FINAL -->
  <div id="screen-result" class="screen-panel">
    <div class="content-card" style="text-align: center;">
      <h2 style="font-size: 28px; margin-bottom: 8px; color: #1e3a8a;">Teste Concluído!</h2>
      <p style="color: #64748b; margin-bottom: 30px; font-size: 16px;">Suas respostas foram salvas com sucesso na planilha institucional.</p>
      
      <div style="background-color: #f0fdf4; border: 2px solid #bbf7d0; border-radius: 20px; padding: 30px; display: inline-block; width: 100%;">
        <span style="font-size: 13px; font-weight: 700; color: #166534; text-transform: uppercase; letter-spacing: 1px; display: block; margin-bottom: 12px;">Sua Âncora Dominante:</span>
        <div id="result-anchor" style="font-size: 24px; font-weight: 700; color: #166534;">Calculando...</div>
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
    { text: "Dou muito valor a benefícios de longo prazo e estabilidade.", cat: 3 },
    { text: "Quero criar produtos ou serviços que tenham a minha identidade.", cat: 4 },
    { text: "Não trabalharia em uma instituição que vai contra meus princípios morais.", cat: 5 },
    { text: "Fico entediado com facilidade se as tarefas forem rotineiras.", cat: 6 },
    { text: "Equilibrar trabalho e lazer é mais importante do que uma promoção.", cat: 7 },
    { text: "Focar em resolver problemas técnicos complexos é o meu ponto forte.", cat: 0 },
    { text: "Acho estimulante monitorar metas e a produtividade de outras pessoas.", cat: 1 },
