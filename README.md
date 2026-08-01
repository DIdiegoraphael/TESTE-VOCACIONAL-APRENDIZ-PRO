<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Aprendiz Pro</title>
  <script src="https://tailwindcss.com"></script>
  <link href="https://googleapis.com" rel="stylesheet">
  <script src="https://jsdelivr.net"></script>
  <style>
    body { font-family: 'Space Grotesk', sans-serif; background: #0b1a3a; }
    .font-arcade { font-family: 'Press Start 2P', monospace; text-shadow: 2px 2px 0px #000; }
    .screen { display: none; }
    .screen.active { display: block; animation: slideUp 0.4s ease-out; }
    @keyframes slideUp { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    .likert-btn { transition: all 0.2s ease; background: #162a56; border: 1px solid #233d7a; color: #e2e8f0; }
    .likert-btn:hover { background: #1e3a75; border-color: #f4c542; color: #fff; }
    .likert-btn.selected { background: #f4c542; color: #0b1a3a; border-color: #f4c542; font-weight: 700; }
  </style>
</head>
<body class="min-h-screen text-slate-100 flex items-center justify-center p-4">

  <div class="w-full max-w-xl bg(#12234a) bg-opacity-60 backdrop-blur-md rounded-3xl p-6 md:p-8 border border-slate-700/50 shadow-2xl">
    
    <!-- TELA 1: BOAS-VINDAS -->
    <div id="screen-welcome" class="screen active space-y-6">
      <div class="text-center space-y-3">
        <h1 class="font-arcade text-[#f4c542] text-base md:text-lg tracking-wider leading-relaxed">
          TESTE VOCACIONAL<br>APRENDIZ PRO
        </h1>
        <p class="text-xs md:text-sm text-slate-400">Descubra sua âncora de carreira com propósito</p>
      </div>

      <div class="bg-[#102046] rounded-2xl p-5 border border-slate-700/30 space-y-3">
        <h2 class="text-sm font-bold text-[#f4c542] uppercase tracking-wider flex items-center gap-2">
          <i data-lucide="terminal" class="w-4 h-4"></i> Sobre o Teste
        </h2>
        <p class="text-xs md:text-sm text-slate-300 leading-relaxed">
          Baseado no conceito internacional de Edgar Schein (MIT). Identifique seus valores e motivações profissionais dominante de forma rápida e intuitiva.
        </p>
      </div>

      <!-- INPUTS MODERNOS -->
      <div class="space-y-4">
        <div>
          <label class="block text-xs font-bold uppercase tracking-wider text-slate-400 mb-2">Nome Completo</label>
          <input id="respondent-name" type="text" placeholder="Digite seu nome..." class="w-full rounded-xl bg-[#162a56] border border-slate-700/50 px-4 py-3 outline-none text-sm text-white placeholder-slate-500 focus:border-[#f4c542] transition-all">
        </div>
        <div>
          <label class="block text-xs font-bold uppercase tracking-wider text-slate-400 mb-2">Turma</label>
          <input id="respondent-class" type="text" placeholder="Ex: t01" class="w-28 rounded-xl bg-[#162a56] border border-slate-700/50 px-4 py-3 outline-none text-sm text-white placeholder-slate-500 focus:border-[#f4c542] transition-all uppercase">
        </div>
      </div>

      <button onclick="startTest()" class="w-full bg-[#f4c542] hover:bg-[#e0b334] text-[#0b1a3a] font-bold text-sm tracking-widest py-4 rounded-xl shadow-lg transition-all uppercase">
        Iniciar Missão
      </button>
    </div>

    <!-- TELA 2: CARD DO QUESTIONÁRIO -->
    <div id="screen-quiz" class="screen space-y-6">
      <div class="flex justify-between items-center text-xs font-bold tracking-wider text-slate-400">
        <span id="quiz-progress-text">QUESTÃO 1 DE 40</span>
        <div class="w-1/3 bg-slate-800 h-1.5 rounded-full overflow-hidden">
          <div id="quiz-progress-bar" class="bg-[#f4c542] h-full transition-all duration-300" style="width: 2.5%;"></div>
        </div>
      </div>

      <div class="min-h-[120px] flex items-center">
        <p id="question-text" class="text-base md:text-lg font-medium text-white leading-relaxed">Carregando pergunta...</p>
      </div>

      <div class="grid grid-cols-1 gap-2.5">
        <button class="likert-btn py-3.5 px-4 rounded-xl text-left text-sm flex items-center justify-between" onclick="selectScore(5)">5 - Concordo Totalmente <i data-lucide="check" class="w-4 h-4 opacity-40"></i></button>
        <button class="likert-btn py-3.5 px-4 rounded-xl text-left text-sm flex items-center justify-between" onclick="selectScore(4)">4 - Concordo Parcialmente <i data-lucide="chevron-right" class="w-4 h-4 opacity-40"></i></button>
        <button class="likert-btn py-3.5 px-4 rounded-xl text-left text-sm flex items-center justify-between" onclick="selectScore(3)">3 - Neutro / Não sei <i data-lucide="minus" class="w-4 h-4 opacity-40"></i></button>
        <button class="likert-btn py-3.5 px-4 rounded-xl text-left text-sm flex items-center justify-between" onclick="selectScore(2)">2 - Discordo Parcialmente <i data-lucide="chevron-left" class="w-4 h-4 opacity-40"></i></button>
        <button class="likert-btn py-3.5 px-4 rounded-xl text-left text-sm flex items-center justify-between" onclick="selectScore(1)">1 - Discordo Totalmente <i data-lucide="x" class="w-4 h-4 opacity-40"></i></button>
      </div>
    </div>

    <!-- TELA 3: CARREGAMENTO -->
    <div id="screen-loading" class="screen text-center py-12 space-y-4">
      <div class="animate-spin inline-block w-8 h-8 border-4 border-[#f4c542] border-t-transparent rounded-full"></div>
      <h2 class="text-sm font-bold tracking-widest text-slate-300 uppercase">Computando Afinidades...</h2>
    </div>

    <!-- TELA 4: RESULTADO -->
    <div id="screen-result" class="screen text-center space-y-6">
      <div class="inline-flex p-3 bg-emerald-500/10 rounded-full text-emerald-400">
        <i data-lucide="award" class="w-8 h-8"></i>
      </div>
      <div class="space-y-1">
        <h2 class="text-xl font-bold text-white">Perfil Concluído!</h2>
        <p class="text-xs text-slate-400">Seus dados foram sincronizados na planilha.</p>
      </div>
      <div class="bg-[#102046] rounded-2xl p-6 border border-slate-700/40">
        <span class="text-xs font-bold text-[#f4c542] uppercase tracking-widest block mb-2">Sua Âncora Dominante:</span>
        <div id="result-anchor" class="text-base md:text-lg font-bold text-white bg-[#162a56] px-4 py-3 rounded-xl border border-slate-700/50 inline-block">Calculando...</div>
      </div>
    </div>

  </div>

  <script>
    lucide.createIcons();
    let userName = "", userClass = "", currentQuestionIndex = 0, userAnswers = [];

    const ancorasNomes = {
      0: "Competência Técnica", 1: "Competência Gerencial", 2: "Autonomia", 
      3: "Segurança / Estabilidade", 4: "Criatividade Empreendedora", 
      5: "Dedicação a uma Causa", 6: "Puro Desafio", 7: "Estilo de Vida"
    };

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
      { text: "Quero usar minhas habilidades profissionais para fazer o bem.", cat: 5 },
      { text: "Superar concorrentes e desafios difíceis me traz satisfação.", cat: 6 },
      { text: "Gosto de empregos que permitam trabalhar em regime de home-office flexível.", cat: 7 },
      { text: "Recuso cargos de liderança pura se me afastarem da minha área técnica.", cat: 0 },
      { text: "Quero chegar a um cargo de alta diretoria executiva no futuro.", cat: 1 },
      { text: "Me sinto sufocado se tiver que bater ponto no mesmo horário todo dia.", cat: 2 },
      { text: "Saber que meu salário está garantido todo mês diminui minha ansiedade.", cat: 3 },
      { text: "Para mim, criar algo inovador é o verdadeiro significado de sucesso.", cat: 4 },
      { text: "Busco uma profissão que melhore diretamente a vida dos jovens ou da comunidade.", cat: 5 },
      { text: "Vencer desafios complexos é o que mais me move.", cat: 6 },
      { text: "Se um trabalho exigir que eu sacrifique minha vida pessoal, eu desisto.", cat: 7 },
