# ID: BUG-01 

## Titulo: Login as vezes redireciona para página de oçamento

## Descrição: Ao Clicar em Login antes do DOM da pagina carregar o botão 'Login para candidatos' redireciona para página de orçamento.
O mesmo Não ocorre quando se aguarda alguns segundo antes de cliquar em Login.

Nota: O bug só ocorre quando o site é acessado através de um site de busca.
O mesmo não ocorre quando acessa o site diretamente através do HTPP.

## Passos para Reproduzir:
- No navegador Acessar site de busca Google.com ou outro site de busca
- Pesquisar por ´Gupy´ e clicar em buscar
- Localizar e clicar no link: **Gupy | Impulsione o seu RH**
- Assim que Localizar o botão de evento acordeão escrito 'Login' no canto superior direito, Clique Imedatamente antes da página carregar completamente
- Clique em 'Login para candidatos'
- Observe ser redirecionádo para página de Orçamento

Nota: Mesmo com a caixa(acordeão) onde aparece 'Login para candidatos' e 'Login para empresas' visivel, ao clicar em 'Login para candidatos' o Usuário é redirecionado para página de orçamentos.

## Analise tecnica:
- Ao inspecionar a página com Devtools pode-se observar a classe: Acordion-content, que quando o a caixa acordeão está expandida e visivel, deveria exibir: 'Class= Acordion-content open' porém quando o Bug ocorre, a caixa acordeão está visivel porém a classe exibe: Acordion-contet, (nota-se que não tem o open, mostrando erro de sequência).
Print desse erro em: /.evidências/prints

Nota: Ao Inspecionar os elementos DOM em 'estilos' através do devtools, nota-se que a opção 'pointer-events: none' está ativada quando a caixa acordeão expandida e visivel, quando o normal seria estár desativado com o acordeão expandido e ativado com o acordeão retraído.
Print desse erro em: /.evidências/prints

## Resultado esperado:
 - Ao clicar no Acordeão 'Login' e depois clicar em 'Login para candidatos' o usuário deveria ser redirecionado para página de login.

## Resultado Obtido:
 - Ao clicar no Acordeão 'Login' antes do Carregamento DOM da pagina e depois clicar em 'Login para candidatos' o usuário é redirecionado para página de orçamentos

## Impactos:
- Ao ter problema no carregamento da página Causado por sinal de internet isntável ou servidor, ou manuseiro inesperado do usúario, a funcionaçliade de Login fica comprometida podendo causar confusão e transtorno no usuário ao tentar Logar na página.

Nível de Prioridade: Médio
Nota: Mesmo sendo um Bug Intermitente, a isntabilidade do DOM da página pode acarretar e mais erros inesperados

## Sugestão de correção:
- Rever a Lógica de eventos DOM e no Script da página
- Impossibilitar o Clique do usuário até que a pagina esteja totalmente carregada

Observações:
- Evidências em Gifs e prints do Bug pode ser encontrao em: /.evidências/gifs , /.evidencias/prints

- Este relatório não depende de código automatizado para demonstrar o erro, devido à natureza intermitente e dependência do carregamento parcial da página.


