# Clean Code JavaScript — Caderno Temático com NotebookLM
   
> Explorando IA como ferramenta de aprendizagem ativa: curadoria, engenharia de prompts e construção de um miniguia de estudos sobre boas práticas em JavaScript.
 
<div align="right"> 
<a href=https://notebooklm.google.com/notebook/0ad614a6-a63c-4813-81f5-11412e79173c">Clique aqui para acessar!</a>
</div>

## Contexto e Objetivos
 
### Por que Clean Code em JavaScript?
 
JavaScript é uma das linguagens mais usadas no mundo, justamente por isso, é também uma das mais "bagunçadas" na prática. Para quem está começando, é natural se preocupar com aprender a fazer o código funcionar, mas também é necessário aprender a fazê-lo comunicar.
 
### Objetivos de Estudo
 
- Compreender os **princípios fundamentais** de código limpo aplicados ao JavaScript;
- Aprender a **nomear variáveis e funções** de forma semântica e intencional;
- Entender quando e como **refatorar** código funcional, mas difícil de manter;
- Construir um **glossário pessoal** dos conceitos mais relevantes;
- Criar uma **biblioteca de prompts** reutilizáveis para revisão futura via IA.
---

## Curadoria de Fontes
 
As fontes abaixo foram selecionadas como as mais importantes por serem abertas, confiáveis e complementares entre si. Todas foram inseridas no NotebookLM para embasar as respostas geradas.
 
| # | Título | Tipo | Link |
|---|--------|------|------|
| 1 | **Clean Code JavaScript** — ryanmcdermott | Repositório GitHub (texto) | [github.com/ryanmcdermott/clean-code-javascript](https://github.com/ryanmcdermott/clean-code-javascript) |
| 2 | **Eloquent JavaScript** — Cap. 4 e 5 (Funções e Estruturas) | Livro aberto (online) | [eloquentjavascript.net](https://eloquentjavascript.net/) |
| 3 | **MDN Web Docs — JavaScript Guide** | Documentação oficial | [developer.mozilla.org/en-US/docs/Web/JavaScript/Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide) |
| 4 | **Refactoring Guru — Refactoring em JS** | Artigos técnicos | [refactoring.guru/refactoring](https://refactoring.guru/refactoring) |
| 5 | **Google JavaScript Style Guide** | Guia de estilo oficial | [google.github.io/styleguide/jsguide.html](https://google.github.io/styleguide/jsguide.html) |
---
 
## Engenharia de Prompts & Cicatrizes
 
Esta seção documenta o processo real de exploração do NotebookLM, incluindo o que funcionou, o que não funcionou e como os prompts foram ajustados.
 
### Rodada 1 - Ponto de partida
 
**Prompt inicial:**
```
O que é Clean Code?
```
 
**Problema:** Resposta muito ampla, apesar de ser baseada nas fontes, os conceitos não foram aprofundados.
 
**Ajuste:**
```
Com base nas fontes do caderno, quais são os principais princípios de Clean Code aplicados especificamente ao JavaScript?
```
 
**Resultado:** A IA listou princípios com referências diretas as fontes e se aprofundou nos princípios, incluindo exemplos de código.
 
**Aprendizado:** Especificar "com base nas fontes" e "aplicado a JavaScript" muda completamente a qualidade da resposta.
 
---
### Rodada 2 - Nomeação de variáveis
 
**Prompt:**
```
Quais são as boas práticas de nomenclatura de variáveis e funções em JavaScript segundo as fontes?
```
 
**Resultado:** Resposta sólida, com exemplos de nomenclatura, regras e formatação.
 
**Variação testada:**
```
Me dê 5 exemplos reais de nomes de variáveis ruins em JS e como reescrevê-los com Clean Code.
```
 
**Resultado:** A IA também apresebtou exemplos de nomenclatura, regras e formatação, além disso, adicionou um formato de antes/depois muito útil para revisão.
 
---
### Rodada 3 - Comentários no código
 
**Prompt:**
```
Quando devo e quando NÃO devo comentar meu código JavaScript? O que as fontes dizem sobre isso?
```
 
**Resultado:** A resposta trouxe a distinção entre comentários que explicam o quê (desnecessários se o código for claro) vs. comentários que explicam por quê (válidos quando o contexto não é óbvio).
 
---
### Rodada 5 - Prompts para revisão futura
 
**Prompt:**
```
Com base em tudo que discutimos, crie uma lista de perguntas que eu possa usar para revisar Clean Code em JavaScript no futuro.
```
 
**Resultado:** Gerou mais de 10 perguntas para revisão. Usei as melhores na seção de prompts reutilizáveis abaixo.
 
---
## 📖 Miniguia de Estudo
 
### 1. Resumos Estruturados
 
#### Nomeação (Variáveis e Funções)
 
- Use nomes que **revelam intenção**. Se você precisa de um comentário para explicar o nome, o nome está errado.
- Variáveis booleanas devem começar com `is`, `has`, `can` → `isActive`, `hasPermission`
- Evite abreviações obscuras: `usr` → `user`, `calc` → `calculateTotal`
- Funções devem ter nomes de **verbos**: `getUser()`, `sendEmail()`, `validateInput()`
```js
// ❌ Ruim
const d = new Date();
const u = getU();
function proc(x) { ... }
 
// ✅ Bom
const currentDate = new Date();
const activeUser = getActiveUser();
function processPayment(order) { ... }
```
 
---

#### Funções
 
- **Uma função, uma responsabilidade.** Se você precisa de "e" para descrever o que ela faz, ela faz coisas demais.
- Prefira **menos parâmetros**: mais de 3 parâmetros é um sinal de alerta. Use um objeto de configuração.
- Evite **efeitos colaterais** não declarados: funções não devem modificar variáveis externas sem que isso fique evidente.
- Prefira **retornar valores** a modificar estado direto.
```js
// ❌ Ruim — faz duas coisas e tem efeito colateral
function saveAndNotify(user) {
  db.save(user);
  sendEmailNotification(user.email);
}
 
// ✅ Bom — responsabilidades separadas
function saveUser(user) { return db.save(user); }
function notifyUser(email) { return sendEmailNotification(email); }
```
 
---
#### Comentários
 
- **Bom código se explica.** Comentário não substitui nome ruim.
- Comente o **porquê**, não o **o quê**.
- Remova comentários desatualizados — são piores que nenhum comentário.
- Comentários TODO são aceitáveis em contexto de aprendizado, mas não em produção sem resolução prevista.
```js
// ❌ Ruim — o comentário repete o código
let age = 25; // define a idade como 25
 
// ✅ Bom — o comentário explica uma decisão não óbvia
// Usamos índice 1 porque a API retorna com base 1, não 0
const firstItem = items[1];
```
 
---
#### Estrutura e Formatação
 
- Use **ESLint** e **Prettier** para automatizar consistência.
- Mantenha **linhas curtas** (máximo ~80-100 caracteres).
- Agrupe código relacionado; separe grupos com uma linha em branco.
- Evite aninhamento profundo (mais de 2-3 níveis de `if`/`for`): use **early return** ou extração de funções.
```js
// ❌ Ruim — aninhamento profundo
function processOrder(order) {
  if (order) {
    if (order.items.length > 0) {
      if (order.isPaid) {
        // processa
      }
    }
  }
}
 
// ✅ Bom — early return
function processOrder(order) {
  if (!order) return;
  if (order.items.length === 0) return;
  if (!order.isPaid) return;
  // processa
}
```
 
---
### 2. Glossário de Conceitos
 
| Termo | Definição |
|-------|-----------|
| **Clean Code** | Código escrito para ser lido por humanos. Claro, simples, sem surpresas |
| **Naming** | Prática de escolher nomes que revelam intenção sem necessidade de comentários |
| **Single Responsibility** | Princípio de que cada função/módulo deve ter apenas uma razão para mudar |
| **Side Effect** | Efeito colateral: quando uma função modifica estado externo além de retornar um valor |
| **Early Return** | Técnica de retornar cedo em funções para evitar aninhamento desnecessário |
| **Refactoring** | Processo de reescrever código existente para melhorar legibilidade sem alterar comportamento |
| **Magic Number** | Número literal no código sem nome ou contexto, deve ser substituído por constante nomeada |
| **DRY (Don't Repeat Yourself)** | Princípio de evitar duplicação de lógica, extraia código repetido em funções reutilizáveis |
| **KISS (Keep It Simple)** | Prefira a solução mais simples que funcione, complexidade desnecessária é um bug em potencial |
| **Linter** | Ferramenta (ex: ESLint) que analisa o código automaticamente em busca de problemas de estilo e erros |
| **Prettier** | Formatador de código que padroniza indentação, aspas, vírgulas etc. automaticamente |
| **Code Smell** | Sinal no código que indica um problema potencial de design, mesmo que o código funcione |
 
---