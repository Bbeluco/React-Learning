Os estados surgem por conta de uma necessidade que existe no desenvolvimento web (nesse caso, principalmente por conta de como o React trabalha).

Acontece basicamente o seguinte, vamos supor que temos o seguinte codigo (propsXstate/exemplo1.jsx). Se rodarmos esse codigo vamos perceber que mesmo clicando no botao next ele nao passa para a proxima imagem. Isso acontece (nesse caso), pq quando o componente renderiza ele pega todas as variaveis e reseta ela.

Basicamente a cada render que ele fizer ele nao salva nada do anterior, entao eh como se a gente nunca tivesse atualizado nada (o que de fato acontece eh que toda variavel tem seu valor inicial atribuido novamente).

Outro ponto agravante nesse caso eh que o React eh estruturado de forma que ele nao sabe que precisa atualizar a tela. Ele so sabe se precisar atualizar ou nao se utilizarmos alguma outra coisa diferente de variaveis. Em outras palavras eh correto dizer o seguinte: **O React nao atualiza UI baseado em variaveis padrao do JS**

# Variaveis de estado
Para nos auxiliar com esse problema o React possui variaveis de estado. Ela pode facilmente ser criada atraves do hook **useState**. Esse hook permite que a variavel tenha as 2 coisas que o React quer pra atualizar a tela:

1. Retencao de valor entre os renders
2. Uma funcao que de trigger na atualizacao de tela

Em suma, o useState criara uma referencia e utilizara ela pra sempre que a pagina atualizar ela possa ver se mudou algo ou nao.

### Como o React sabe que variavel mudar?
Voce notou que no texto acima eu disse que ha uma referencia entre o useState e a variavel que deve ser atualizada. Mas se a sintaxe do useState eh assim:

```javascript
const [button, setButton] = useState("");
```

Como exatamente o useState sabe qual variavel alterar? (considerando que eu posso ter multiplos useStates na minha aplicacao).

A resposta pra isso esta na forma que o React cria suas variaveis de estado. Ha uma regra no React que diz que ele nao pode criar qualquer hook dentro de condicionais, estruturas de repeticao, etc. Essa regra existe pq o React tem um sistema engenhoso para criar seus hooks, funciona assim:

- Cada hook que o react cria ele adiciona em um array em memoria
- Quando atualizamos uma variavel o que acontece na verdade eh que vamos nesse array e por posicao atualizamos algo la
- O React detecta que houve essa mudanca e renderiza novamente o componente

# State como snapshot
O que essa parte da documentacao diz eh bem simples de entender. O que o estado faz no react eh uma acao simples. Quando vamos atualizar um componente (por questao de atualizacao de estado por exemplo). O react pega todo o componente, recalcula ele usando as variaveis de estado que ele tem disponivel naquele momento e te devolve um novo componente.

O que eh importante ressaltar nesse caso eh que ele faz esse processo de forma sincrona, funciona basicamente assim:

1. Trigger de atualizacao de componente
2. Recalculo do componente
3. Renderizacao de novo componente


A descricao que eu acabei de falar acima diz exatamente que nao eh possivel aninhar diversos "setStates", isso pq logo no primeiro o componente todo iria sofrer um re-render e ele nao saberia que outros triggers foram chamados. Um exemplo desse comportamento pode ser encontrado no arquivo propsXstate/exemplo2.jsx

Nesse arquivo citado acima eh interessante ressaltar do pq o pessoal chama de snapshot. Acontece o seguinte fluxo (nesse arquivo em especifico)

1. setNumber(number + 1): number eh igual a 0 logo, 0+1 = 1;
2. setNumber(number + 1): number eh igual a 0 logo, 0+1 = 1;
3. setNumber(number + 1): number eh igual a 0 logo, 0+1 = 1;

Eh chamado de snapshot pq basicamente congelamos o tempo, pegamos todas as informacoes que precisamos e depois recalculamos o componente
