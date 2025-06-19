# 📝 ProvaReply
Um simples script para pegar as resposta de questões da Prova Paulista, na Sala do Futuro.

```js
javascript:(function(){const style=document.createElement('style');style.textContent=`#chatBoxContainer{position:fixed;bottom:20px;right:20px;width:300px;height:400px;background:#555;color:white;font-family:sans-serif;border-radius:10px;overflow:hidden;display:none;flex-direction:column;z-index:9999;}#chatBoxHeader{padding:10px;font-weight:bold;text-align:center;background-color:#444;}#chatBoxMessages{flex:1;padding:10px;overflow-y:auto;font-size:14px;}#chatBoxButton{padding:15px;text-align:center;background:#222;cursor:pointer;font-weight:bold;user-select:none;}#chatBoxButton:hover{background:#111;}#instructionModal{position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.7);color:white;display:flex;align-items:center;justify-content:center;font-size:20px;z-index:10000;}#instructionModalContent{background:#333;padding:30px;border-radius:8px;text-align:center;}`;document.head.appendChild(style);const modal=document.createElement('div');modal.id='instructionModal';modal.innerHTML=`<div id="instructionModalContent">Pressione <b>P</b> para mostrar/ocultar o chat.<br><br><button onclick="this.closest('#instructionModal').remove()">OK</button></div>`;document.body.appendChild(modal);const chat=document.createElement('div');chat.id='chatBoxContainer';chat.innerHTML=`<div id="chatBoxHeader">ProvaReply</div><div id="chatBoxMessages"></div><div id="chatBoxButton">RESPOSTA</div>`;document.body.appendChild(chat);document.addEventListener('keydown',(e)=>{if(e.key.toLowerCase()==='p'){chat.style.display=chat.style.display==='none'?'flex':'none';}});async function fetchAndUpdateResponse(){const questionText=document.querySelector("#root > div.MuiBox-root.css-z0hhne > div.MuiBox-root.css-a60g7b > div > div.simplebar-wrapper > div.simplebar-mask > div > div > div > div.css-gsuwte > div > div > div.MuiGrid-root.MuiGrid-container.MuiGrid-item.MuiGrid-spacing-xs-3.MuiGrid-grid-xs-12.css-1lhjp8 > div.MuiGrid-root.MuiGrid-item.MuiGrid-grid-xs-12.css-1fgqv6k > div > div.MuiBox-root.css-1ap3w3k > div.MuiPaper-root.MuiPaper-elevation.MuiPaper-rounded.MuiPaper-elevation3.MuiCard-root.css-os4ngo > div.MuiBox-root.css-j7qwjs")?.textContent||'';const answersContainer=document.querySelector("#root > div.MuiBox-root.css-z0hhne > div.MuiBox-root.css-a60g7b > div > div.simplebar-wrapper > div.simplebar-mask > div > div > div > div.css-gsuwte > div > div > div.MuiGrid-root.MuiGrid-container.MuiGrid-item.MuiGrid-spacing-xs-3.MuiGrid-grid-xs-12.css-1lhjp8 > div.MuiGrid-root.MuiGrid-item.MuiGrid-grid-xs-12.css-1fgqv6k > div > div.MuiBox-root.css-1ap3w3k > div.MuiPaper-root.MuiPaper-elevation.MuiPaper-rounded.MuiPaper-elevation3.MuiCard-root.css-os4ngo > div.MuiBox-root.css-0 > div");let answersText='';if(answersContainer){const paragraphs=answersContainer.querySelectorAll('p');answersText=Array.from(paragraphs).map(p=>p.textContent).join('\n');}try{const response=await fetch('https://sch-api.vercel.app/api/utils/replier',{method:'POST',headers:{'content-type':'application/json'},body:JSON.stringify({question:questionText,answers:answersText})});const json=await response.json();const chatMessages=document.getElementById('chatBoxMessages');if(chatMessages.lastChild){chatMessages.lastChild.textContent=json.results.result;}else{const msg=document.createElement('div');msg.textContent=json.results.result;chatMessages.appendChild(msg);}}catch(error){console.error('Erro ao buscar resposta da API:',error);}}document.getElementById('chatBoxButton').addEventListener('click',fetchAndUpdateResponse);})();
```

**⚠️ FUNCIONA MELHOR PARA QUESTÕES EM QUE O TEXTO DA QUESTÃO POSSUÍ APENAS TEXTO, SEM IMAGENS! (O MESMO PARA AS ALTERNATIVAS)**

# 📚 Tutorial
## 🌐 Chromebook 
- Copie o script acima;
- Caso a barra de favoritos não esteja habilitada, aperte `CTRL + SHIFT + B`;
- Pressione `CTRL + D`;
- Clique no seletor de pastas (geralmente "Barra de favoritos" é a padrão);
- Clique em "Escolher outra pasta";
- Coloque um nome, como **ProvaReply**;
- Na URL, cole o script acima e salve;
- Vá em uma prova (em que a questão e as alternativas estão vísiveis;
- Clique no favorito que foi criado na barra de favoritos;
- Siga as instruções ;)
## 💻 Non-Chromebook
- Copie o script acima;
- Vá em uma prova (em que a questão e as alternativas estão vísiveis;
- Pressione `CTRL + L`;
- Escreva "**javascript:**" e cole o script;
- Pressione `ENTER`;
- Siga as instruções ;)

# 📄 Licença
**MIT License**

# ✉️ Contato
**Se você precisar entrar em contato sobre qualquer tópico, envie um e-mail para `juniorschueller.br@gmail.com` ou por Discord `juniorschueller`.**
**Mensagens aleatórias não serão respondidas.**
