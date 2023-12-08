# Entendendo Blocos em Ruby on Rails: Um Guia para Iniciantes 🚀

Oi, pessoal! Hoje vamos mergulhar no mundo do Ruby on Rails e desvendar um dos seus recursos mais legais: os blocos. Se você está começando no Rails, esse artigo é perfeito pra você!

## O que São Blocos em Ruby? 🤔

Então, o que são esses tais de blocos em Ruby? Imagine que você está preparando uma receita e, de repente, um amigo chega com um ingrediente secreto que transforma tudo em uma delícia ainda maior. Os blocos são exatamente assim: pedaços de código que você adiciona a um método para dar aquele toque especial. Eles chegam, fazem a mágica acontecer e saem discretamente, deixando o método continuar seu trabalho. Super mágicos e incrivelmente úteis!

### Duas Maneiras de Criar Blocos:

No Ruby, você pode criar blocos de duas maneiras, cada uma com sua própria vibe e estilo. Vamos dar uma olhada:

1. **Usando Chaves `{}`:** Esta é a opção para quando você quer ser direto e objetivo. Pensa num tweet: curto e direto ao ponto. Esse estilo é ideal para blocos de uma única linha. É como se você estivesse dando um comando rápido para o seu código.

   Por exemplo:
   ```ruby
   [1, 2, 3].each { |numero| puts numero }
   ```
   Aqui, para cada elemento no array `[1, 2, 3]`, o bloco `{ |numero| puts numero }` é executado. Este bloco pega cada `numero` e dá um `puts` nele, ou seja, imprime na tela.

2. **Usando `do..end`:** Agora, se você quer ter uma conversa mais detalhada com o seu código, essa é a escolha. É como escrever uma carta em vez de um tweet. Esse formato é perfeito para blocos com várias linhas, dando mais espaço para expressar suas ideias.

   Dê uma olhada nesse exemplo:
   ```ruby
   [1, 2, 3].each do |numero|
     puts numero
     puts numero * 10
   end
   ```
   Neste caso, o bloco começa com `do` e termina com `end`. Ele não só imprime cada `numero`, mas também o multiplica por 10 e imprime o resultado. Esse formato dá mais liberdade para você brincar com várias linhas de código dentro do bloco.

Então, resumindo, use `{}` para algo rápido e `do..end` para algo mais elaborado. Ambos fazem a mesma coisa de maneiras um pouco diferentes, e a escolha entre eles geralmente depende da complexidade do que você está tentando fazer com o bloco.

### Blocos na Ação! 🎬

Blocos são como assistentes pessoais dos métodos. Eles entram em cena, fazem seu trabalho e saem, deixando o método continuar sua jornada.

## Exemplos Bacanas com Blocos

### Iterando Arrays com Blocos

Ruby torna super simples percorrer (ou iterar) cada elemento de uma coleção, como um array. No exemplo que demos:

```ruby
numeros = [1, 2, 3, 4, 5]
numeros.each { |numero| puts "Número: #{numero}" }
```

Aqui está o que está acontecendo passo a passo:

1. **Definindo um Array:** Primeiro, criamos um array chamado `numeros`, que contém os números de 1 a 5:
   ```ruby
   numeros = [1, 2, 3, 4, 5]
   ```

2. **Usando o Método `.each`:** Em seguida, usamos o método `.each`. Este método é super útil em Ruby e é usado para iterar sobre cada elemento de uma coleção, como o nosso array `numeros`. 

3. **Passando um Bloco para `.each`:** Agora vem a parte divertida! Passamos um bloco para o método `.each`:
   ```ruby
   { |numero| puts "Número: #{numero}" }
   ```
   Este bloco será executado uma vez para cada elemento do array. Dentro das chaves `{}`, temos:
   
   - `|numero|`: Esta é a parte onde definimos uma variável temporária para cada elemento do array. A cada iteração, `numero` será igual a um elemento do array (primeiro 1, depois 2, e assim por diante).
   - `puts "Número: #{numero}"`: Aqui, estamos dizendo para o Ruby imprimir ("puts") o valor de `numero`. O `#{numero}` dentro da string é a forma de Ruby inserir o valor da variável `numero` na string.

4. **O Resultado:** O que acontece quando este código é executado? Para cada número no array `numeros`, o Ruby vai imprimir "Número: x", onde x é o número atual na iteração.

Então, de maneira simples e elegante, você acaba percorrendo todos os elementos do array e fazendo algo com eles - neste caso, imprimindo-os. Essa é a beleza dos blocos em Ruby: eles permitem que você execute um pedaço de código repetidas vezes, de forma limpa e eficiente, para cada elemento de uma coleção.

### Personalizando Métodos com Blocos em Ruby

Em Ruby, não apenas você pode usar blocos com métodos predefinidos, como `.each`, mas também pode criar seus próprios métodos que aceitam blocos. Isso abre um mundo de possibilidades para personalizar como seus métodos funcionam. Vamos destrinchar o exemplo dado:

```ruby
def saudar
  puts "Oi!"
  yield if block_given?
  puts "Fui!"
end

saudar { puts "Beleza pura!" }
```

1. **Definindo um Método Personalizado:** 
   - `def saudar`: Aqui, começamos definindo um novo método chamado `saudar`. `def` é a forma como declaramos um método em Ruby.

2. **O Corpo do Método:**
   - `puts "Oi!"`: Quando chamamos o método `saudar`, ele primeiro executa esta linha, que imprime a palavra "Oi!".
   - `yield if block_given?`: Esta é a parte interessante. `yield` é uma palavra-chave em Ruby que pausa a execução do método e passa o controle para o bloco fornecido na chamada do método. `if block_given?` é um método que verifica se um bloco foi passado para o método. Então, se `saudar` for chamado com um bloco, esse bloco será executado neste ponto.
   - `puts "Fui!"`: Depois de executar o bloco, o método retoma e executa esta linha, que imprime "Fui!".

3. **Chamando o Método com um Bloco:**
   - `saudar { puts "Beleza pura!" }`: Aqui, estamos chamando o método `saudar` e passando um bloco para ele. Dentro do bloco, temos a instrução `puts "Beleza pura!"`. Portanto, quando o `yield` no método `saudar` é alcançado, o código dentro do bloco `{ puts "Beleza pura!" }` é executado.

O resultado final quando chamamos `saudar { puts "Beleza pura!" }` será:

```
Oi!
Beleza pura!
Fui!
```

Este exemplo ilustra como você pode criar métodos flexíveis e adaptáveis em Ruby, que podem se comportar de maneira diferente dependendo do bloco que você passa para eles. Isso permite uma programação muito dinâmica e criativa, onde o mesmo método pode ter diferentes comportamentos com base nos blocos fornecidos.

### Tratamento de Erros com Elegância em Ruby

Em Ruby, o uso de blocos também se estende ao tratamento de erros, tornando o processo mais organizado e menos propenso a causar problemas no seu código. Vamos analisar o exemplo fornecido:

```ruby
begin
  # tentando algo arriscado
rescue => erro
  # ops, deu ruim, mas tá tudo sob controle
end
```

1. **Estrutura `begin...rescue...end`:** Esta estrutura é usada para lidar com exceções, que são erros que podem ocorrer durante a execução do programa.

2. **Bloco `begin`:** Dentro do bloco `begin`, você coloca o código que pode potencialmente causar um erro. Por exemplo, pode ser uma operação que interage com um arquivo ou uma chamada de rede.

3. **Bloco `rescue`:** Se um erro ocorrer dentro do bloco `begin`, o fluxo do programa é imediatamente direcionado para o bloco `rescue`. Aqui, a variável `erro` captura a exceção que foi lançada. Isso permite que você acesse informações sobre o erro e execute o código para lidar com ele, como registrar o erro ou tentar uma ação alternativa.

4. **Finalizando com `end`:** A estrutura é concluída com `end`, indicando o fim do tratamento de exceção.

Por exemplo:

```ruby
begin
  # Código que pode falhar, como File.open('arquivo_inexistente.txt')
rescue => erro
  puts "Ocorreu um erro: #{erro.message}"
end
```

Neste cenário, se o arquivo não existir e um erro for lançado, o bloco `rescue` captura o erro e executa o `puts`, exibindo a mensagem do erro. Isso evita que o programa inteiro pare de funcionar devido a um erro isolado. 

Essa abordagem com blocos para tratamento de erros é uma forma eficiente de manter a robustez e a confiabilidade do seu código em Ruby.

## Perguntinhas Comuns

**Quando usar um bloco em Ruby?**  
👉 Use blocos quando precisar de um pouco mais de flexibilidade e personalização em seus métodos. Eles são ótimos para adicionar instruções específicas a métodos, especialmente em loops ou operações personalizadas.

   **Exemplo:**
   ```ruby
   [1, 2, 3].map { |numero| numero * 2 }
   ```
   Neste caso, o bloco `{ |numero| numero * 2 }` é usado com o método `.map` para dobrar cada número no array.

**Blocos mexem em variáveis de fora?**  
👉 Sim! Blocos podem interagir com variáveis definidas fora deles, permitindo que você manipule essas variáveis dentro do bloco.

   **Exemplo:**
   ```ruby
   mensagem = "Olá"
   [1, 2, 3].each { |numero| mensagem += " #{numero}" }
   puts mensagem
   ```
   Aqui, a variável `mensagem` é modificada dentro do bloco anexado ao método `.each`.

**Blocos e lambdas são irmãos gêmeos?**  
👉 Eles são bem similares, mas têm diferenças importantes, especialmente em como tratam os retornos e os argumentos.

   **Exemplo com Bloco:**
   ```ruby
   def teste_bloco
     yield
     return "Fim do bloco"
   end
   puts teste_bloco { return "Retorno do bloco" }
   ```
   Aqui, o `return` dentro do bloco vai interromper o método inteiro.

   **Exemplo com Lambda:**
   ```ruby
   meu_lambda = lambda { return "Retorno do lambda" }
   def teste_lambda(l)
     l.call
     return "Fim do lambda"
   end
   puts teste_lambda(meu_lambda)
   ```
   Neste caso, o `return` no lambda não afeta o fluxo fora dele; assim, "Fim do lambda" será impresso após o retorno do lambda.

## Conclusão

E aí, curtiu? Blocos no Ruby tornam a codificação mais funcional. Experimente usá-los no seu próximo projeto Rails e veja a mágica acontecer. Até a próxima, galera! 🚀 

