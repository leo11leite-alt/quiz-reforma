[index.html](https://github.com/user-attachments/files/33615168/index.html)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Quiz: A Reforma Protestante (Aula 1)</title>
<style>
:root{--bg:#f4f6fa;--surface:#fff;--ink:#14213d;--muted:#5a6478;--line:#d5dbe8;--accent:#2f4b9c;--accent-ink:#fff;--ok:#1e7f4f;--ok-bg:#e3f4ea;--bad:#b23a48;--bad-bg:#fbe7ea;color-scheme:light;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0f1626;--surface:#182036;--ink:#e8ecf5;--muted:#a3adc2;--line:#2b3654;--accent:#8fa8ff;--accent-ink:#0f1626;--ok:#6fd49b;--ok-bg:#16301f;--bad:#ff8d9a;--bad-bg:#3a1b22;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#0f1626;--surface:#182036;--ink:#e8ecf5;--muted:#a3adc2;--line:#2b3654;--accent:#8fa8ff;--accent-ink:#0f1626;--ok:#6fd49b;--ok-bg:#16301f;--bad:#ff8d9a;--bad-bg:#3a1b22;color-scheme:dark}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*,*::before,*::after{box-sizing:inherit}
body{margin:0;background:var(--bg);color:var(--ink);font:17px/1.55 system-ui,-apple-system,"Segoe UI",Roboto,Arial,sans-serif}
main{max-width:640px;margin:0 auto;padding:24px 18px 48px}
h1{font:700 26px/1.25 Georgia,"Times New Roman",serif;margin:0 0 6px}
.sub{color:var(--muted);margin:0 0 20px;font-size:15px}
.bar{height:6px;background:var(--line);border-radius:3px;overflow:hidden;margin-bottom:6px}
.bar i{display:block;height:100%;width:0;background:var(--accent);transition:width .25s}
.count{color:var(--muted);font-size:14px;margin:0 0 18px}
.card{background:var(--surface);border:1px solid var(--line);border-radius:12px;padding:20px 18px}
.q{font:600 21px/1.4 Georgia,"Times New Roman",serif;margin:0 0 16px}
.opts{display:grid;gap:10px}
.opt{font:inherit;text-align:left;color:var(--ink);background:var(--bg);border:1.5px solid var(--line);border-radius:10px;padding:13px 14px;cursor:pointer;width:100%}
.opt:hover:not(:disabled){border-color:var(--accent)}
.opt:focus-visible,.btn:focus-visible{outline:3px solid var(--accent);outline-offset:2px}
.opt:disabled{cursor:default}
.opt.ok{background:var(--ok-bg);border-color:var(--ok);color:var(--ink)}
.opt.bad{background:var(--bad-bg);border-color:var(--bad);color:var(--ink)}
.fb{margin:16px 0 0;padding:12px 14px;border-radius:10px;background:var(--bg);border-left:4px solid var(--accent)}
.fb b{display:block;margin-bottom:2px}
.fb.ok b{color:var(--ok)}.fb.bad b{color:var(--bad)}
.btn{font:600 16px/1 system-ui,sans-serif;background:var(--accent);color:var(--accent-ink);border:0;border-radius:10px;padding:14px 20px;margin-top:16px;cursor:pointer}
.score{font:700 44px/1 Georgia,serif;margin:4px 0 10px}
.hide{display:none}
</style>
</head>
<body>
<main>
<h1>A Reforma Protestante</h1>
<p class="sub">Quiz da aula 1 · 12 perguntas</p>
<div id="quiz">
  <div class="bar"><i id="fill"></i></div>
  <p class="count" id="count"></p>
  <div class="card">
    <p class="q" id="q"></p>
    <div class="opts" id="opts"></div>
    <div class="fb hide" id="fb" role="status"></div>
    <button class="btn hide" id="next" type="button"></button>
  </div>
</div>
<div class="card hide" id="result">
  <p class="count">Seu resultado</p>
  <p class="score" id="score"></p>
  <p id="msg"></p>
  <button class="btn" id="again" type="button">Refazer o quiz</button>
</div>
</main>
<script>
var Q=[
{q:"O que John Wycliffe e seus colaboradores impulsionaram por volta de 1382?",o:["A publicação do Novo Testamento grego","A afixação de 95 teses em Londres","A tradução da Bíblia para o inglês","A fundação da Companhia de Jesus"],a:2,e:"Wycliffe, professor de Oxford, defendia a Bíblia como autoridade acima do papa e da tradição. Seus seguidores, os lolardos, levaram a Bíblia em inglês ao povo."},
{q:"O que aconteceu com Jan Hus depois do Concílio de Constança?",o:["Retratou-se e foi perdoado","Foi exilado na Inglaterra","Foi queimado vivo em 1415","Morreu de causas naturais em Praga"],a:2,e:"Hus recusou-se a retratar-se e foi queimado em 6 de julho de 1415. Seus seguidores deram origem aos hussitas."},
{q:"Qual foi o motivo imediato das 95 teses?",o:["A venda de indulgências","A tradução da Bíblia para o alemão","A proibição do casamento de padres","A invenção da imprensa"],a:0,e:"Lutero reagiu à venda de indulgências, certificados que prometiam reduzir a punição pelos pecados em troca de dinheiro."},
{q:"Em que data, tradicionalmente, Lutero afixou as 95 teses em Wittenberg?",o:["6 de julho de 1415","18 de abril de 1521","1º de janeiro de 1530","31 de outubro de 1517"],a:3,e:"A data tradicional é 31 de outubro de 1517, por isso essa data é lembrada como o Dia da Reforma."},
{q:"O que Lutero respondeu na Dieta de Worms (1521), quando mandaram que se retratasse?",o:["Retratou-se para evitar a fogueira","Recusou-se, dizendo que sua consciência estava presa à Palavra de Deus","Fugiu antes de ser ouvido","Pediu que o papa decidisse por ele"],a:1,e:"Lutero não se retratou. Foi excomungado e, depois, escondido em Wartburg, onde traduziu o Novo Testamento para o alemão."},
{q:"Qual é o versículo que diz “O justo viverá pela fé”?",o:["Efésios 2:8","Salmo 119:105","Romanos 1:17","João 14:6"],a:2,e:"Romanos 1:17 cita Habacuque 2:4 e foi central na redescoberta do evangelho por Lutero."},
{q:"Quais são as cinco solas da Reforma?",o:["Sola Scriptura, Sola Fide, Sola Gratia, Solus Christus e Soli Deo Gloria","Sola Scriptura, Sola Fide, Sola Gratia, Sola Ecclesia e Soli Deo Gloria","Sola Scriptura, Sola Fide, Sola Opera, Solus Christus e Soli Deo Gloria","Sola Scriptura, Sola Traditio, Sola Gratia, Solus Christus e Soli Deo Gloria"],a:0,e:"As cinco solas são: somente a Escritura, somente a fé, somente a graça, somente Cristo e glória somente a Deus."},
{q:"Qual sola afirma que a Bíblia é a autoridade final e suficiente para a fé e a vida?",o:["Solus Christus","Sola Fide","Sola Scriptura","Soli Deo Gloria"],a:2,e:"A Sola Scriptura se apoia em textos como 2 Timóteo 3:16-17: toda a Escritura é inspirada por Deus e útil para ensinar e corrigir."},
{q:"Qual sola afirma que somos declarados justos diante de Deus pela fé, e não pelas obras?",o:["Sola Gratia","Sola Fide","Sola Scriptura","Solus Christus"],a:1,e:"A Sola Fide ensina que a justificação vem pela fé, como em Romanos 3:28 e Efésios 2:8-9. As obras são fruto da fé, não a sua causa."},
{q:"O que a Sola Gratia afirma?",o:["A graça só chega a quem já tem muitas obras","A graça é dada depois que a pessoa merece","A graça vale só para quem frequenta a igreja","A salvação é dom imerecido de Deus, do começo ao fim"],a:3,e:"Segundo Efésios 2:8-9, somos salvos pela graça, e isso não vem de nós: é dom de Deus. Deus age primeiro."},
{q:"Segundo 1 Timóteo 2:5, quantos mediadores existem entre Deus e os homens?",o:["Dois: Cristo e os apóstolos","Muitos: os santos e os anjos","Nenhum: cada um chega a Deus por mérito próprio","Um só: Cristo Jesus"],a:3,e:"É o coração do Solus Christus: somente Cristo é o mediador, e seu sacrifício na cruz é suficiente."},
{q:"Qual é a melhor descrição de Soli Deo Gloria?",o:["Somente o papa pode interpretar a Bíblia","Toda a vida, inclusive o trabalho comum, deve ser vivida para a glória de Deus","A glória é só para quem tem muitas obras","Somente os pastores podem glorificar a Deus"],a:1,e:"Soli Deo Gloria é a conclusão das outras solas: se a salvação é de Deus, a glória é só dele (Romanos 11:36; 1 Coríntios 10:31)."}
];
var i=0,score=0,locked=false;
var $=function(id){return document.getElementById(id)};
function show(){
  var d=Q[i];locked=false;
  $("count").textContent="Pergunta "+(i+1)+" de "+Q.length;
  $("fill").style.width=(i/Q.length*100)+"%";
  $("q").textContent=d.q;
  var box=$("opts");box.innerHTML="";
  d.o.forEach(function(t,k){
    var b=document.createElement("button");
    b.type="button";b.className="opt";b.textContent=t;
    b.onclick=function(){pick(k)};
    box.appendChild(b);
  });
  $("fb").className="fb hide";$("next").className="btn hide";
}
function pick(k){
  if(locked)return;locked=true;
  var d=Q[i],btns=$("opts").children,right=(k===d.a);
  if(right)score++;
  for(var n=0;n<btns.length;n++){
    btns[n].disabled=true;
    if(n===d.a)btns[n].classList.add("ok");
    else if(n===k)btns[n].classList.add("bad");
  }
  var fb=$("fb");fb.className="fb "+(right?"ok":"bad");
  fb.innerHTML="";
  var h=document.createElement("b");h.textContent=right?"Resposta certa!":"Não foi dessa vez.";
  fb.appendChild(h);fb.appendChild(document.createTextNode(d.e));
  var nx=$("next");nx.className="btn";
  nx.textContent=(i===Q.length-1)?"Ver resultado":"Próxima pergunta";
  nx.focus();
}
$("next").onclick=function(){
  i++;
  if(i<Q.length){show();window.scrollTo(0,0);}
  else finish();
};
function finish(){
  $("quiz").className="hide";$("result").className="card";
  $("score").textContent=score+" de "+Q.length;
  var m=score>=10?"Excelente! Você domina o conteúdo da aula."
       :score>=7?"Muito bem! Revise as explicações das perguntas que errou."
       :"Boa tentativa! Releia as explicações e tente de novo.";
  $("msg").textContent=m;
  window.scrollTo(0,0);
}
$("again").onclick=function(){
  i=0;score=0;$("result").className="card hide";$("quiz").className="";show();
};
show();
</script>
</body>
</html>
