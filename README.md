# 🐞 Bug Report – Redirecionamento incorreto no login da Gupy

## Descrição do Projeto

Este repositório tem como objetivo documentar um **bug real e intermitente** encontrado no site da **Gupy**, identificado através de **testes exploratórios manuais**.

O problema foi descoberto durante a navegação no site utilizando um buscador (DuckDuckGo, Google etc.). Inicialmente, o comportamento parecia aleatório, mas após investigação detalhada, foi possível entender que o bug ocorre **quando há interação com o botão "Login" antes do carregamento completo do DOM da página**.

---

## Sobre o Bug

O erro acontece quando:

1. O site da Gupy é acessado via buscador (não ocorre via acesso direto pela URL).
2. O botão **"Login"**, que utiliza um **componente acordeão (accordion)**, é clicado rapidamente após o carregamento inicial da página.
3. Mesmo que a caixa acordeão se expanda visualmente, o DOM ainda não está pronto para aceitar interações.
4. O clique em **"Login para candidatos"** redireciona o usuário para uma página de **orçamento**, e não para a página de login.

![BUG-01 Gif](evidencias/Gifs/bug-01.gif)

---

## Detalhes Técnicos

Durante a inspeção com o DevTools do navegador, foram identificados os seguintes pontos críticos que indicam erro de sincronização entre a interface e o DOM:

- A caixa acordeão usa a classe `accordion-content`.  
  Quando **funcionando corretamente**, ela possui a classe:  
  `accordion-content open`

- Durante o bug, mesmo com o acordeão expandido visualmente, a classe aparece apenas como:  
  `accordion-content` (sem o `open`), indicando que a lógica interna do componente ainda não foi ativada.

- Além disso, o botão de interação está com a propriedade CSS:  
  `pointer-events: none`  
  Isso **impede a interatividade com os elementos**, mesmo que estejam visíveis ao usuário.

  ![BUG-01 Print](evidencias/prints/bug-01.JPG)
  ![Funcionamento Normal](evidencias/prints/funcionamento_normal.JPG)
  

---

##  Comportamento Observado

- **Cenário com bug**:
  - O usuário acessa o site via buscador
  - Clica no botão "Login" rapidamente após o carregamento inicial
  - Clica em "Login para candidatos"
  - É redirecionado incorretamente para a página de orçamento (`/orcamento`)

- **Cenário normal**:
  - O usuário aguarda o carregamento completo da página
  - O clique no botão "Login" expande corretamente o acordeão
  - O clique em "Login para candidatos" redireciona corretamente para a tela de login

---

## Evidências

As evidências foram coletadas com prints e gifs, que demonstram o comportamento esperado e o comportamento incorreto:

- `/evidencias/gifs/BUG-01.gif`
- `/evidencias/prints/BUG-01.png`

---

## Impacto

- Compromete a principal funcionalidade de acesso à plataforma
- Pode confundir usuários com conexão instável ou que interagem rapidamente
- Indica problemas na lógica de controle de eventos do DOM, podendo afetar outras áreas

---

## Conclusão

Este projeto demonstra a importância dos testes exploratórios e de se observar o comportamento **não apenas visual**, mas estrutural do DOM em aplicações modernas.

O foco do projeto é **manual**, por conta do bug ser **intermitente e altamente dependente do tempo de carregamento**, com documentação precisa, clara e com análise técnica para fornecer insights reais a uma equipe de desenvolvimento ou QA profissional.

---

## Tecnologias Utilizadas

- Navegador: Chrome / Edge / Firefox
- DevTools para análise DOM e estilos
- Ferramentas de captura de tela (print e gif)
- Markdown para documentação

## BUG report feito no JIRA

![Funcionamento Normal](evidencias/Gifs/reporte_no_jira.gif)

---
**Meydson santos**  
Relatório elaborado como parte de um portfólio de QA Manual, com foco em identificação e documentação de falhas reais em ambientes de produção.

