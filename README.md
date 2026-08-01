<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Teste das Âncoras de Carreira</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <link href="https://googleapis.com" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/lucide@0.263.0/dist/umd/lucide.min.js"></script>
  <style>
    * { font-family: 'Poppins', sans-serif; }
    :root { --blue: #123A8C; --gold: #F4C542; --light: #EAF3FF; --dark: #0A0A0A; --muted: #DCEBFF; }
    .screen { display: none; animation: fadeIn .4s ease; }
    .screen.active { display: block; }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(12px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes slideIn { from { opacity: 0; transform: translateX(30px); } to { opacity: 1; transform: translateX(0); } }
    .q-card { animation: slideIn .35s ease; }
    .likert-btn { transition: all .2s; background: #F8FCFF; color: #0A0A0A; border: 2px solid #E5E7EB; }
    .likert-btn.selected { background: var(--blue); color: #fff; transform: scale(1.05); box-shadow: 0 4px 12px rgba(0,87,217,.3); border-color: var(--blue); }
    .progress-fill { transition: width .4s ease; }
    .btn-primary { background: var(--blue); color: #fff; border-radius: 12px; padding: 14px 32px; font-weight: 600; transition: all .2s; border: none; cursor: pointer; }
    .btn-primary:hover { background: #0046b3; transform: translateY(-1px); box-shadow: 0 6px 20px rgba(0,87,217,.3); }
    .btn-secondary { background: var(--gold); color: #0A0A0A; border: 2px solid var(--gold); border-radius: 12px; padding: 12px 28px; font-weight: 700; transition: all .2s; cursor: pointer; }
    .btn-secondary:hover { background: #D9A900; }
    .card { background: #F8FCFF; color: #0A0A0A; border-radius: 16px; box-shadow: 0 2px 12px rgba(0,0,0,.16); padding: 24px; }
  </style>
</head>
<body class="min-h-screen w-full" style="background: rgb(18, 58, 140);">
  <div class="w-full max-w-3xl mx-auto px-4 py-8">
   
   <!-- TELA 1: BOAS-VINDAS -->
   <div id="screen-welcome" class="screen active">
    <div class="text-center mb-8">
     <div class="inline-flex items-center justify-center w-16 h-16 rounded-full mb-4" style="background:var(--light)">
      <i data-lucide="compass" style="width:32px;height:32px;color:var(--blue)"></i>
     </div>
     <h1 class="text-3xl md:text-4xl font-bold mb-3 text-white">TESTE VOCACIONAL<br>APRENDIZ PRO</h1>
     <p class="text-lg text-blue-100 font-medium">Descubra a sua âncora de carreira e se desenvolva profissionalmente com propósito</p>
    </div>
    <div class="card mb-6">
     <h2 class="text-xl font-bold mb-3 text-gray-900">O que é o teste vocacional Aprendiz Pro?</h2>
     <p class="text-gray-700 leading-relaxed">O nosso teste vocacional é orientado pelo conceito das <strong>Âncoras de Carreira</strong>, modelo criado pelo psicólogo organizacional Edgar H. Schein, do MIT. Elas representam os valores, motivações e competências que guiam suas decisões profissionais. Este teste identifica qual das âncoras é dominante no seu perfil.</p>
    </div>
    <div class="card mb-8" style="border-left:4px solid var(--gold)">
     <h3 class="font-bold mb-2 text-gray-900">Como responder</h3>
     <p class="text-gray-700">Responda de forma espontânea, pensando na sua carreira ideal e nos seus valores fundamentais. Não pense apenas no seu momento atual.</p>
    </div>
    <div class="card mb-6">
     <label for="respondent-name" class="block font-bold mb-2 text-gray-900">Nome do respondente (obrigatório)</label> 
     <input id="respondent-name" type="text" required class="w-full rounded-xl border-2 border-gray-200 px-4 py-3 outline-none focus:border-blue-600" style="background:#F8FCFF;color:#0A0A0A">
     
     <div class="mt-4 max-w-xs">
      <label for="respondent-class" class="block text-sm font-bold mb-2 text-gray-900">Turma (obrigatório)</label> 
      <input id="respondent-class" type="text" required placeholder="t01" class="w-full rounded-lg border-2 border-gray-200 px-3 py-2 text-sm outline-none focus:border-blue-600" style="background:#F8FCFF;color:#0A0A0A">
      <p class="mt-1 text-xs text-gray-500">Exemplo: t01</p>
     </div>
    </div>
    <div class="text-center">
     <button class="btn-secondary text-lg" onclick="startTest()">Iniciar Teste</button>
    </div>
   </div>

   <!-- TELA 2: QUESTIONÁRIO DIRECIONADO -->
   <div id="screen-quiz" class="screen">
     <div class="card mb-4 flex justify-between items-center py-3">
       <span id="quiz-progress-text" class="font-bold text-gray-700">Questão 1 de 40</span>
       <div class="w-1/2 bg-gray-200 rounded-full h-3">
         <div id="quiz-progress-bar" class="progress-fill h-3 rounded-full" style="background:var(--blue); width: 2.5%;"></div>
       </div>
     </div>
     <div class="card q-card mb-6">
       <p id="question-text" class="text-xl font-medium text-gray-900 mb-6">Carregando pergunta...</p>
       <div class="grid grid-cols-1 gap-3">
         <button class="likert-btn py-3 px-4 rounded-xl font-medium text-left" onclick="selectScore(5)">5 - Discordo Totalmente</button>
         <button class="likert-btn py-3 px-4 rounded-xl font-medium text-left" onclick="selectScore(4)">4 - Discordo Parcialmente</button>
         <button class="likert-btn py-3 px-4 rounded-xl font-medium text-left" onclick="selectScore(3)">3 - Neutro / Não sei</button>
         <button class="likert-btn py-3 px-4 rounded-xl font-medium text-left" onclick="selectScore(2)">2 - Concordo Parcialmente</button>
         <button class="likert-btn py-3 px-4 rounded-xl font-medium text-left" onclick="selectScore(1)">1 - Concordo Totalmente</button>
       </div>
     </div>
   </div>

   <!-- TELA 3: ENVIANDO DADOS (LOADING INVISÍVEL) -->
   <div id="screen-loading" class="screen text-center py-12">
     <div class="card">
       <h2 class="text-2xl font-bold mb-4">Processando seu Perfil...</h2>
       <p class="text-gray-600 mb-6">Estamos computando suas respostas e salvando o resultado na planilha institucional.</p>
       <div class="animate-spin inline-block w-10 h-10 border-4 border-blue-600 border-t-transparent rounded-full mb-4"></div>
     </div>
   </div>

   <!-- TELA 4: RESULTADO FINAL -->
   <div id="screen-result" class="screen">
     <div class="card text-center mb-6">
       <div class="inline-flex items-center justify-center w-16 h-16 rounded-full mb-4 bg-green-100">
         <i data-lucide="check-circle" style="width:32px;height:32px;color:green"></i>
       </div>
       <h2 class="text-3xl font-bold text-gray-900 mb-2">Teste Concluído!</h2>
       <p class="text-gray-600">Seus dados foram salvos com sucesso na planilha institucional.</p>
     </div>
     <div class="card">
       <h3 class="text-xl font-bold mb-2">Sua Âncora Dominante é:</h3>
       <div id="result-anchor" class="text-2xl font-black tracking-wide text-blue-800 p-4 bg-blue-50 rounded-xl mb-4 border-l-4 border-blue-600">Calculando...</div>
       <p id="result-description" class="text-gray-700 leading-relaxed">Sua âncora representa seu principal motivador de carreira.</p>
     </div>
   </div>

  </div>

  <script>
    // Inicializa os ícones do Lucide
    lucide.createIcons();

    let userName = "";
    let userClass = "";
    let currentQuestionIndex = 0;
    let userAnswers = [];

    // Mapeamento das 40 questões para as 8 categorias tradicionais (5 questões por categoria)
    const ancorasNomes = {
      0: "Competência Técnica / Funcional",
      1: "Competência Gerencial Geral",
      2: "Autonomia / Independência",
      3: "Segurança / Estabilidade",
      4: "Criatividade Empreendedora",
      5: "Dedicação a uma Causa / Serviço",
      6: "Puro Desafio",
      7: "Estilo de Vida"
    };

    // Banco de dados condensado das 40 afirmações para jovens
    const questions = [
      { text: "Quero ser extremamente bom na minha área técnica específica.", cat: 0 },
      { text: "Me motiva a ideia de liderar e gerenciar grandes equipes.", cat: 1 },
      { text: "Eu prefiro trabalhar de forma livre, definindo meus próprios horários.", cat: 2 },
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
      { text: "Fico mais feliz quando trabalho sozinho sem supervisão direta.", cat: 2 },
      { text: "Prefiro crescer dentro de uma mesma instituição sólida por anos.", cat: 3 },
      { text: "Gosto de assumir riscos financeiros para testar novas ideias comerciais.", cat: 4 },
