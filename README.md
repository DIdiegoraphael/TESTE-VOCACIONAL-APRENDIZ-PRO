<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Teste das Âncoras de Carreira - Aprendiz Pro</title>
  <script src="https://tailwindcss.com"></script>
  <!-- Fontes: Poppins para leitura leve e Press Start 2P para o estilo Arcade Gamer -->
  <link href="https://googleapis.com" rel="stylesheet">
  <script src="https://jsdelivr.net"></script>
  <style>
    body { font-family: 'Poppins', sans-serif; background-color: #123A8C; }
    .arcade-title { font-family: 'Press Start 2P', cursive; line-height: 1.5; text-shadow: 3px 3px 0px #0A0A0A; }
    .screen { display: none; animation: fadeIn .5s cubic-bezier(0.4, 0, 0.2, 1); }
    .screen.active { display: block; }
    @keyframes fadeIn { from { opacity: 0; transform: scale(0.98) translateY(8px); } to { opacity: 1; transform: scale(1) translateY(0); } }
    .likert-btn { transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1); background: #FFFFFF; color: #0A0A0A; border: 2px solid #E5E7EB; }
    .likert-btn:hover { border-color: #123A8C; background: #F0F6FF; transform: translateY(-1px); }
    .likert-btn.selected { background: #123A8C; color: #FFFFFF; transform: scale(1.02); box-shadow: 0 8px 20px rgba(18,58,140,0.25); border-color: #123A8C; }
    .progress-fill { transition: width 0.4s cubic-bezier(0.4, 0, 0.2, 1); }
    .card-glow { box-shadow: 0 10px 30px -5px rgba(0, 0, 0, 0.3); }
  </style>
</head>
<body class="min-h-screen w-full flex items-center justify-center py-6 md:py-12 px-4 select-none text-gray-800">
  <div class="w-full max-w-2xl">
   
   <!-- TELA 1: BOAS-VINDAS -->
   <div id="screen-welcome" class="screen active">
    <div class="text-center mb-8">
     <div class="inline-flex items-center justify-center w-16 h-16 rounded-2xl mb-5 bg-[#F4C542] shadow-lg animate-bounce">
      <i data-lucide="gamepad-2" class="w-8 h-8 text-[#123A8C]"></i>
     </div>
     <!-- Título com a fonte Arcade Gamer solicitada -->
     <h1 class="arcade-title text-xl md:text-2xl font-bold mb-4 text-[#F4C542]">
       TESTE VOCACIONAL<br>APRENDIZ PRO
     </h1>
     <p class="text-base md:text-lg text-blue-100 font-light max-w-md mx-auto"> Descubra a sua âncora de carreira de um jeito dinâmico e direto ao ponto. </p>
    </div>

    <div class="bg-white rounded-3xl p-6 md:p-8 card-glow mb-6 border border-blue-900/10">
     <h2 class="text-xl font-bold mb-3 text-[#123A8C] flex items-center gap-2">
       <i data-lucide="info" class="w-5 h-5"></i> O que é o teste?
     </h2>
     <p class="text-gray-600 leading-relaxed text-sm md:text-base">
       Baseado no conceito internacional de Edgar Schein (MIT), este teste avalia suas verdadeiras motivações profissionais. Descubra o que te move no trabalho de forma rápida.
     </p>
     <div class="mt-5 pt-4 border-t border-gray-100 text-xs md:text-sm text-gray-500 flex items-center gap-2">
       <i data-lucide="clock" class="w-4 h-4 text-[#F4C542]"></i> Leva apenas 10 minutos • 40 afirmações rápidas.
     </div>
    </div>

    <!-- Identificação Limpa do Usuário -->
    <div class="bg-white rounded-3xl p-6 md:p-8 card-glow mb-8 space-y-4">
     <div>
       <label for="respondent-name" class="block font-semibold text-sm text-gray-700 mb-2">Seu Nome Completo</label> 
       <input id="respondent-name" type="text" placeholder="Digite seu nome..." required class="w-full rounded-xl bg-gray-50 border-2 border-transparent px-4 py-3 outline-none transition-all focus:border-[#123A8C] focus:bg-white text-gray-900 font-medium">
     </div>
     
     <div class="w-full sm:w-1/2">
      <label for="respondent-class" class="block font-semibold text-sm text-gray-700 mb-2">Sua Turma</label> 
      <input id="respondent-class" type="text" placeholder="Ex: t01" required class="w-full rounded-xl bg-gray-50 border-2 border-transparent px-4 py-2 outline-none transition-all focus:border-[#123A8C] focus:bg-white text-gray-900 font-medium uppercase">
     </div>
    </div>

    <div class="text-center">
     <button class="w-full sm:w-auto bg-[#F4C542] hover:bg-[#e0b334] text-[#123A8C] font-extrabold text-lg px-12 py-4 rounded-2xl shadow-lg hover:shadow-xl transition-all transform hover:-translate-y-0.5 active:translate-y-0" onclick="startTest()">
       COMEÇAR AGORA
     </button>
    </div>
   </div>

   <!-- TELA 2: CARD DO QUESTIONÁRIO -->
   <div id="screen-quiz" class="screen">
     <!-- Barra de Progresso Clean -->
     <div class="bg-white/10 rounded-2xl p-4 mb-4 flex justify-between items-center backdrop-blur-sm">
       <span id="quiz-progress-text" class="font-bold text-xs md:text-sm text-blue-100 tracking-wide">QUESTÃO 1 DE 40</span>
       <div class="w-1/2 bg-white/20 rounded-full h-2.5 overflow-hidden">
         <div id="quiz-progress-bar" class="progress-fill h-full bg-[#F4C542]" style="width: 2.5%;"></div>
       </div>
     </div>

     <!-- Card de Pergunta Estilo Mobile App -->
     <div class="bg-white rounded-3xl p-6 md:p-8 card-glow min-h-[380px] flex flex-col justify-between">
       <div>
         <div class="text-xs font-bold text-gray-400 uppercase tracking-widest mb-2 flex items-center gap-1">
           <i data-lucide="help-circle" class="w-4 h-4 text-[#123A8C]"></i> Avalie a afirmação:
         </div>
         <p id="question-text" class="text-lg md:text-xl font-semibold text-gray-800 leading-snug">Carregando pergunta...</p>
       </div>

       <!-- Escala Likert Otimizada Visualmente -->
       <div class="grid grid-cols-1 gap-2.5 mt-6">
         <button class="likert-btn py-3 px-4 rounded-xl font-medium text-left text-sm md:text-base flex items-center gap-3" onclick="selectScore(5)">
           <span class="w-7 h-7 rounded-lg bg-gray-100 flex items-center justify-center font-bold text-xs text-gray-500">5</span> Concordo Totalmente
         </button>
         <button class="likert-btn py-3 px-4 rounded-xl font-medium text-left text-sm md:text-base flex items-center gap-3" onclick="selectScore(4)">
           <span class="w-7 h-7 rounded-lg bg-gray-100 flex items-center justify-center font-bold text-xs text-gray-500">4</span> Concordo Parcialmente
         </button>
         <button class="likert-btn py-3 px-4 rounded-xl font-medium text-left text-sm md:text-base flex items-center gap-3" onclick="selectScore(3)">
           <span class="w-7 h-7 rounded-lg bg-gray-100 flex items-center justify-center font-bold text-xs text-gray-500">3</span> Neutro / Não sei
         </button>
         <button class="likert-btn py-3 px-4 rounded-xl font-medium text-left text-sm md:text-base flex items-center gap-3" onclick="selectScore(2)">
           <span class="w-7 h-7 rounded-lg bg-gray-100 flex items-center justify-center font-bold text-xs text-gray-500">2</span> Discordo Parcialmente
         </button>
         <button class="likert-btn py-3 px-4 rounded-xl font-medium text-left text-sm md:text-base flex items-center gap-3" onclick="selectScore(1)">
           <span class="w-7 h-7 rounded-lg bg-gray-100 flex items-center justify-center font-bold text-xs text-gray-500">1</span> Discordo Totalmente
         </button>
       </div>
     </div>
   </div>

   <!-- TELA 3: CARREGAMENTO DA PLANILHA -->
   <div id="screen-loading" class="screen text-center py-12">
     <div class="bg-white rounded-3xl p-8 card-glow flex flex-col items-center justify-center space-y-4">
       <div class="animate-spin inline-block w-12 h-12 border-4 border-[#123A8C] border-t-transparent rounded-full mb-2"></div>
       <h2 class="text-2xl font-bold text-[#123A8C]">Processando Perfil...</h2>
       <p class="text-gray-500 text-sm max-w-xs">Salvando seus resultados de forma direta e segura no banco de dados.</p>
     </div>
   </div>

   <!-- TELA 4: EXIBIÇÃO DE RESULTADO PREMIUM -->
   <div id="screen-result" class="screen">
     <div class="bg-white rounded-3xl p-6 md:p-8 card-glow text-center mb-6">
       <div class="inline-flex items-center justify-center w-16 h-16 rounded-full mb-4 bg-green-50 text-green-500">
         <i data-lucide="shield-check" class="w-8 h-8"></i>
       </div>
       <h2 class="text-2xl md:text-3xl font-extrabold text-gray-900 mb-1">Perfil Concluído!</h2>
       <p class="text-sm text-gray-400">Respostas computadas e enviadas com sucesso.</p>
       
       <div class="mt-6 p-6 bg-blue-50/50 rounded-2xl border-2 border-dashed border-blue-100">
         <span class="text-xs font-bold text-[#123A8C] uppercase tracking-widest block mb-2">Sua Âncora Dominante é:</span>
         <div id="result-anchor" class="text-xl md:text-2xl font-black text-[#123A8C] px-4 py-2 bg-white rounded-xl shadow-sm inline-block">Calculando...</div>
       </div>
     </div>
   </div>

  </div>

  <script>
    // Inicialização automática de elementos vetoriais Lucide
    lucide.createIcons();

    let userName = "";
    let userClass = "";
    let currentQuestionIndex = 0;
    let userAnswers = [];

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

    // Banco de questões atualizado para as 8 dimensões de Schein
    const questions = [
      { text: "Quero ser extremamente bom na minha área técnica específica.", cat: 0 },
      { text: "Me motiva a ideia de liderar e gerenciar grandes equipes.", cat: 1 },
      { text: "Eu prefiro trabalhar de forma livre, definindo meus próprios horários.", cat: 2 },
      { text: "Prefiro um emprego estável e seguro a assumir riscos de mercado.", cat: 3 },
      { text: "Sonho em construir e abrir meu próprio negócio do zero.", cat: 4 },
