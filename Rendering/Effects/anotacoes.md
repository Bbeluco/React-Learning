Rendering = Funcao que retorna um valor a ser carregado pelo DOM. Ela deve **ser pura**. Isso significa que sempre para aquela entrada teremos sempre um valor de saida. (OBS: Nao confundir ser pura com nunca ser renderizada novamente na memoria, para mais informacoes consulte a secao Rendering/anotacoes.md).

Event Handlers = Contem side effects (muda o seu contexto ao redor). Eles podem servir para: Enviar requisicao HTTP, abrir conexao com o banco de dados, atualizar o valor de um campo em tela, etc.



# O que sao efeitos?
Efeitos sao side effects que o proprio rendering causa. Sem necessariamente precisar de um trigger a nao ser a montagem do componente.

Vamos imaginar que temos um componente chamado *ChatRoom*

Um evento comum que podemos imaginar seria mandar a mensagem por chat (essa acao parte diretamente do usuario, ele tem o desejo de enviar uma mensagem, logo, dispara um trigger desse event handler).

Agora um **efeito** que podemos pensar seria carregar a sala de chat para esse usuario. Ele nao fez nada a nao ser estar presente naquela sala porem se faz necessario que a gente abra conexao com o socket da sala e bla bla bla

efeitos sao carregados **depois** do commit (carregar a tela para o usuario)

## Cuidados necessarios
Eh importantate tomar cuidado na hora que estiver construindo um componente com efeitos. Se so chamamos o efeito para sincronizar com entidades externas, na teoria nao deveriamos chamar ele toda hora (imagina abrir toda hora uma conexao nova pra um banco de dados).

Uma ideia que o pessoal da para diminuir esse comportamento eh fazer o useEffect retornar algo, esse algo vai ser sempre chamado **antes** do useEffect rodar novamente (confira no codigo Rendering/Effects/exemplo1.jsx)

