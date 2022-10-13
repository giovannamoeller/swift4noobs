# Opcionais

## O que são opcionais?

Uma variável opcional pode, ou não, conter um valor. Caso não haja um valor, ela será `nil`, ou seja, nulo. Se existe um valor, a variável se iguala a esse valor.

Veja o exemplo de código abaixo:

```swift
var nome: String? // perceba o uso do ?, aqui estamos criando uma variável opcional
print(nome) // nil
```

Ou então, se atribuirmos um valor para essa opcional:

```swift
var nome: String?
nome = "Giovanna"
print(nome) // Optional("Giovanna")
```
O uso é bem parecido com variáveis não opcionais, porém o resultado de uma opcional é a nossa variável "embrulhada" dentro de algo escrito `Optional()`. Portanto, precisamos fazer uma **verificação**, justamente para desembrulhar essa opcional.

Vamos imaginar que temos uma caixa, que é nossa opcional. Dentro dessa caixa, pode ter um valor, e quando retiramos o valor de dentro da caixa, a variável se iguala a esse valor. Caso não tenha nada dentro da caixa, então ela nos retornará nil (*nothing at all*, algo nulo, inexistente).

Você pode estar se perguntando: por que eu iria querer utilizar uma opcional no meu código? Muitas vezes, é a própria linguagem que faz o uso de opcionais para tratar questões de segurança. Veja abaixo:

```swift
var numeros: [Int] = [38, 45, 32, 47]
print(numeros.first) // Optional(38)
```

Isso acontece porque o Swift não consegue garantir que exista algum valor dentro desse array, as vezes ele pode estar vazio, certo? Então em vez de quebrar sua aplicação, ele adiciona essa "camada de segurança".

Se o array for vazio, como eu mencionei:

```swift
var numeros: [Int] = []
print(numeros.first) // nil
```

Mas então, como fazer para pegar o valor que vem dentro de um `Optional()`? Como lidamos com opcionais?

## Lidando com opcionais

Podemos dizer que existem cinco maneiras que são mais utilizadas para desembrulhar uma opcional, e vamos discutir mais sobre elas aqui:

### 1. Forçar o desembrulho

Essa é, na verdade, a maneira menos recomendada de lidarmos com uma opcional, pois estamos afirmando que existe um valor dentro dela, mesmo que não exista.

Para forçar o desembrulho, nós usamos um ponto de exclamação no final da variável, dessa maneira:

```swift
var nome: String?
nome = "Giovanna"
print(nome!)
```

É preciso ter muito cuidado quando utilizar essa abordagem, pois pode não existir um valor, ou seja, se for `nil`, a aplicação irá quebrar, causando um *runtime error* (erro de execução, que é aquele erro que crasha a nossa aplicação). 

Em todo caso, é sempre recomendado fazer uma verificação se o valor existe ou não. O caso mais seguro de usar o ! para desembrulhar uma opcional é realizar uma verificação para ver se o valor realmente não é nil, dessa maneira:

```swift
var nome: String?
nome = "Giovanna"

if nome != nil {
  print(nome!)
}
```

### 2. Optional Binding

O método optional binding é uma abordagem bem mais segura para desembrulhar uma opcional. Veja o código abaixo:

```swift
var nomeOpcional: String?
nomeOpcional = "Giovanna"

if let nome = nomeOpcional {
  print(nome)
}
```

Primeiramente, nós criamos uma constante `nome` que iguala ao valor de `nomeOpcional` se essa variável não for nula, ou seja, se ela não for `nil`.

Observe que agora, quando printamos a variável `nome`, ela não retorna mais como `Optional()`, e sim o seu valor concreto. Isso acontece porque a variável `nome` é um valor não-opcional. É desembrulhado pela verificação `if let`.

No Swift 5.7, essa sintaxe ficou ainda melhor:

```swift
var nome: String?
nome = "Giovanna"

if let nome {
  print(nome)
}
```

Você também pode usar múltiplas opcionais dentro da mesma verificação, dessa maneira:

```swift
var nome: String? = "John"
var sobrenome: String? = "Doe"

if let nome = nome, let sobrenome = sobrenome {
  print(nome)
  print(sobrenome)
}
```

### 3. Optional Chaining

Esse método permite que nosso código rode apenas se nossa opcional possuir de fato um valor. Veja o código abaixo para entender melhor o que é o optional chaining:

```swift
var nome: String?
nome = "Giovanna"
print(nome?.first)
```

Ele só irá pegar o primeiro valor da string (através dessa propriedade `first`), caso a variável `nome` não seja `nil`.

Porém, veja que, na verdade, o Swift nos retorna o valor dentro de uma `Optional()`. Por esse motivo, é muito comum combinarmos *optional chaining* com *optional binding*. Veja o código abaixo:

```swift
var nome: String?
nome = "Giovanna"
if let primeiroCaractere = nome?.first {
  print(primeiroCaractere)
}
```

Lembrando que *chaining* vem de encadeamento, então é a ideia de encadear as propriedades para fazer a verificação.

### 4. Guard let

Esse método é muito parecido com o *optional binding* (que é o uso do `if let`, que vimos acima). Porém, se a opcional for nula, ele retorna algo. Veja o código abaixo:

```swift
func autenticar(usuario: String?, senha: String?) {
  guard let usuario = usuario, let senha = senha else { return }
  print(usuario)
  print(senha)
}

autenticar(usuario: "John", senha: "1234")
```

Portanto, se o código retorna alguma coisa, significa que o `guard let` deve ser usado dentro de uma função. No código acima, caso ambas as variáveis sejam `nil`, irá sair da função imediatamente, sem ao menos printar os valores. Vamos fazer o teste? Veja abaixo:

```swift
func autenticar(usuario: String?, senha: String?) {
  guard let usuario = usuario, let senha = senha else { return }
  print(usuario)
  print(senha)
}

autenticar(usuario: nil, senha: nil)
```

Veja que esse método permite utilizar a variável desembrulhada fora do escopo, enquanto isso não é permitido com o uso do `if let`, como vimos acima. Então, se precisarmos utilizar uma variável em outros lugares, o recomendado é fazer o uso do `guard let` em vez do `if let`.

### 5. Nil Coalescing Operator

O Nil Coalescing Operator é um operador que consiste no uso de dois pontos de interrogação: `??`. Ele aceita uma expressão à esquerda, que é a variável opcional, e uma expressão à direita, que é o valor que tomará lugar caso a variável opcional for `nil`. Veja o código abaixo para entender melhor como funciona:

```swift
var nome: String? = "Giovanna"
print(nome ?? "Inexistente")
```

Se a variável `nome` for `nil`, será printado "inexistente".

Ir para a próxima página: [Arrays](08-arrays.md)