O React possui uma forma que eh conhecida como: _Abordagem declarativa_ Isso significa que o componente que vamos criar sera primeiramente declarado (sera dito exatamente o que esse componente fara). Isso eh um contrate com o que tinhamos antigamente em _abordagem imperativas_ (basicamente eh manipular diretamente o DOM atraves de JS para que ele faca exatamente o que voce deseja).

Esse componente que eh carregado esta no que eh conhecido como VDOM (Virtual DOM). Basicamente o React pega a arvore DOM e deixa ela em memoria. Ele faz isso para acelerar a renderizacao de componentes

Um ponto importante do VDOM eh que o React compara se houve diferenca entre os rendering ou nao, se tiver ele faz um calculo do que seria o minimo possivel necessario para alterar e atualiza essa informacao diretamente na DOM, so depois de atualizar o dom ele atualiza a VDOM novamente. Esse processo eh conhecido como **reconciliacao**

# Rendering
Mas afinal, o que seria rendering?
Segundo o blog [UI DEV](https://ui.dev/why-react-renders):

_Rendering eh um jeito bonito de dizer que seu codigo vai chamar a sua funcao e **potencialmente** atualizara sua UI_