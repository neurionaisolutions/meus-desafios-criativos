# Desafio Criativo - Automação com N8N

Este repositório contém minha solução para o **Desafio Criativo: Planejando Automações com N8N Usando Apenas Bons Prompts**.

---

## 🧱 Passo 1: Definição da Automação
- **Tarefa repetitiva a automatizar:** Enviar alertas de status e ETA de entregas/rotas.  
- **Quem será impactado/beneficiado:** Equipe de logística e clientes que aguardam a entrega.  
- **Resultado final esperado:** Clientes recebem automaticamente notificações (WhatsApp/e-mail) quando a entrega sai, está próxima ou chega, sem necessidade de acompanhamento manual no painel.  

---

## 🧱 Passo 2: Contexto e Regras
- **Ferramentas envolvidas:** Sistema de rastreio de entregas, WhatsApp, E-mail.  
- **Fluxo desejado:**
  1. Detectar mudança de status da entrega/rota no sistema de rastreio.  
  2. Capturar ETA atualizado e dados do cliente.  
  3. Enviar alerta automático ao cliente (WhatsApp/e-mail) e registrar notificação enviada.  
- **Regras importantes:**  
  - Só enviar alerta quando houver mudança real de status (ex.: saiu, está próximo, chegou).  
  - Evitar duplicidade de mensagens para o mesmo status.  
  - Se não houver ETA disponível, enviar apenas o status básico.  
  - Garantir que o cliente tenha contato válido (WhatsApp/e-mail) antes de enviar.  

---

## 🧱 Passo 3: Prompt Final

**Atue como um especialista em N8N.**

Crie uma automação para **enviar alertas de status e ETA de entregas/rotas**.

**Público:**  
Equipe de logística e clientes que aguardam a entrega.

**Ferramentas envolvidas:**  
- Sistema de rastreio de entregas  
- WhatsApp  
- E-mail  

**Fluxo:**  
1. Detectar mudança de status da entrega/rota no sistema de rastreio.  
2. Capturar ETA atualizado e dados do cliente.  
3. Enviar alerta automático ao cliente (WhatsApp/e-mail) e registrar notificação enviada.  

**Regras:**  
- Só enviar alerta quando houver mudança real de status (ex.: saiu, está próximo, chegou).  
- Evitar duplicidade de mensagens para o mesmo status.  
- Se não houver ETA disponível, enviar apenas o status básico.  
- Garantir que o cliente tenha contato válido (WhatsApp/e-mail) antes de enviar.  

---

## 🔧 Nós do N8N e Lógica do Workflow
- **Webhook ou HTTP Request:** conecta ao sistema de rastreio e recebe a atualização de status.  
- **IF:** valida se houve mudança real de status.  
- **Function:** processa os dados recebidos, extrai ETA e formata a mensagem.  
- **Set:** organiza os campos necessários (status, ETA, contato do cliente).  
- **WhatsApp API ou Email:** envia a notificação ao cliente.  
- **Database ou Google Sheets:** registra que a notificação foi enviada, evitando duplicidade.  

**Lógica:**  
1. O gatilho é disparado quando o sistema de rastreio informa uma mudança de status.  
2. O nó **IF** verifica se o status é novo e válido.  
3. O nó **Function** prepara a mensagem com status e ETA.  
4. O nó **Set** organiza os dados para envio.  
5. Dependendo do canal disponível, o nó de **WhatsApp** ou **Email** dispara a notificação.  
6. O registro é salvo em banco ou planilha para controle e auditoria.  
