Inicialmente o que precisamos ter ideia eh que o React nao necessariamente precisa ser escrito utilizando JSX. Usamos isso apenas para nos auxiliar no dia a dia a escrever codigo mas ele funciona com outras extensoes

A explicacao do pq o React coloca Javascript e HTML na mesma pagina se da devido a um avanco que ocorreu na internet como um todo. Em suma, com a evolucao da internet o HTML e o Javascript viviam lado a lado entao por conta disso compactaram tudo no mesmo lugar

JSX e React nao sao a mesma coisa.
JSX = file extension
React = Biblioteca

### Pq um JSX nao pode retornar multiplos elementos filhos?
Segundo a [doc](https://react.dev/learn/writing-markup-with-jsx#why-do-multiple-jsx-tags-need-to-be-wrapped) o que acontece nesse caso eh que o JSX retorna sempre o resultado de uma funcao. Atualmente sabemos que nao eh possivel retornarmos multiplos retornos em uma funcao no Javascript. Nesse caso (quando temos 2 ou mais funcoes), o sistema se perde e nao sabe como/qual retornar. A solucao pra isso eh sempre retornarmos um unico resultado no JSX (Ou seja, um unico corpo HTML que emglobe tudo)

### Pq no react temos className ao inves de class para tags HTML?
Acontece nesse caso que tudo o que eh atributo de tag HTML quando processado pelo JSX vira chaves de um objeto Javascript. Como no Javascript a palavra "class" eh reservada precisaram fazer esse tipo de manobra.