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