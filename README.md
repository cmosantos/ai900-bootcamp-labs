# ⭐ ai900-labs-dio — Laboratórios Reconstruídos e Aprofundados para o Bootcamp AI Fundamentals (AI-900)

Este repositório foi criado com o objetivo de **reconstruir** os laboratórios originalmente disponibilizados pela DIO para o bootcamp *Azure AI Fundamentals (AI-900)*, cujos links estão atualmente indisponíveis.  
Aqui você encontrará versões **aprimoradas, aprofundadas e atualizadas**, permitindo que você execute todos os exercícios essenciais exigidos no curso — mesmo sem acesso aos links originais.

Os três pilares deste material são:

- **Bing Copilot** (compreensão de IA generativa)  
- **Azure OpenAI Service** (uso prático de modelos)  
- **Content Filters / Content Safety** (IA responsável na prática)

Este README serve como **documentação oficial**, **artefato de entrega da DIO**, e **portfólio profissional** no GitHub.

---

# 🔍 1. Laboratório — Bing Copilot  
### *Fundamentos, Prática e Comportamento de Modelos Generativos*

O Bing Copilot (Microsoft Copilot) representa a forma mais acessível de interagir com modelos generativos da Microsoft e OpenAI sem necessidade de recursos adicionais. Ele permite que qualquer usuário experimente:

- criação de textos  
- análises estruturadas  
- geração criativa  
- transformação de conteúdo  
- behavior tuning via prompt  

---

## 🎯 Objetivos do Lab
- Explorar como a IA responde a diferentes estilos de prompt.  
- Entender como estrutura, contexto e intenção mudam a resposta.  
- Observar o impacto da ambiguidade e de prompts mal formulados.  
- Desenvolver familiaridade com respostas incorretas e “alucinações”.  
- Compreender o papel da *engenharia de prompt*.

---

## 🧪 Passo a passo — Interações Guiadas

### 🔹 Teste 1: Criação
Prompt:  
> Explique em um parágrafo simples como funciona a IA generativa.

### 🔹 Teste 2: Transformação
Prompt:  
> Reescreva o texto acima em formato motivacional.

### 🔹 Teste 3: Análise
Prompt:  
> Extraia apenas as ideias principais do texto anterior em formato de lista.

### 🔹 Teste 4: Criatividade
Prompt:  
> Escreva um texto curto sobre o uso da IA no dia a dia de um analista de TI, com tom inspirador.

---

## 🧠 Insights Essenciais
- A clareza do prompt determina a qualidade da resposta.  
- O Copilot não acessa dados privados sem que o usuário forneça.  
- Modelos generativos podem completar informação incorreta (*alucinação*).  
- Ajustes finos no prompt mudam totalmente a entrega final.

---

# 🔍 2. Laboratório — Azure OpenAI  
### *Criação, Configuração, Deployments e Execução Avançada de Modelos*

Este laboratório representa o coração técnico do bootcamp.  
Aqui você aprenderá a usar o **Azure OpenAI**, que oferece:

- segurança empresarial  
- controle de acesso  
- métricas de uso  
- logs  
- compliance  
- governança  

Tudo isso diferencia o Azure do uso direto da OpenAI.

---

## 📌 Pré-requisitos
- Conta Azure (trial funciona).  
- Subscription ativa.  
- Permissão de criação de recursos.

---

## ⚙️ Criando o recurso Azure OpenAI
1. Acesse https://portal.azure.com  
2. Pesquise por **Azure OpenAI**  
3. Clique em **Create**  
4. Configure:
   - Resource Group: `rg-ai900`
   - Nome: `openai-[seu-nome]`
   - Região: **East US** ou **Sweden Central**
   - Pricing Tier: *Standard*

---

## 🔑 Obtendo Endpoint e Keys
Após criado:

- Vá em **Keys and Endpoint**
- Copie:
  - Endpoint  
  - Key 1 / Key 2  

Estes valores permitem chamadas via API REST ou SDKs.

---

# 🧪 Primeiro Teste — Execução do Modelo via REST

Use o payload abaixo substituindo KEY e ENDPOINT:

```json
POST {ENDPOINT}/openai/deployments/gpt-4o-mini/chat/completions?api-version=2024-06-01
Content-Type: application/json
api-key: {KEY}

{
  "messages": [
    { "role": "system", "content": "Você é um assistente educado e direto." },
    { "role": "user", "content": "Explique IA generativa em 3 frases." }
  ],
  "max_tokens": 200,
  "temperature": 0.7
}

