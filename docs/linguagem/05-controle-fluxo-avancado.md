# Controle de fluxo avançado

## Loops
No assunto anterior, vimos sobre dois tipos de loop: `while` e `repeat-while`. Agora, vamos ver sobre o loop `for`.

### For

O `for` é ideal para casos em que você sabe quantas vezes algo irá repetir. Veja um exemplo abaixo:

```swift
for i in 0...10 {
    print(i)
}
```

Para entender o que está acontecendo acima, precisamos entender sobre intervalos no Swift.

### Intervalos

Intervalo é um tipo de dado que permite a representação de uma sequência de valores.

Primeiramente, temos o que chamamos de sequencia fechada, que você pode representar como:

```swift
    let intervaloFechado = 0...5
```

A sequencia fechada inclui o primeiro e último valor também. Portanto, essa sequencia representa os valores 0, 1, 2, 3, 4 e 5 no caso acima.

Também temos a sequencia meio-aberta, que podemos representar como:

```swift
    let intervaloMeioAberto = 0..<5
```

A sequencia meio-aberta inclui o primeiro , mas não o último valor. Portanto, essa sequencia representa os valores 0, 1, 2, 3 e 4 no caso acima.

Lembrando que o intervalo sempre precisa ser em ordem crescente. Ou seja, o segundo número sempre precisa ser maior ou igual ao primeiro. Esse tipo de dado é muito usado no `switch` e no `for`.

### Voltando para o for...

Agora, voltando para o `for`, no código acima, o resultado será o print de 0 até 10, incluindo o 10. Veja outro exemplo abaixo:

```swift
let count = 10
var soma = 0
for i in 1...count {
soma += i
}
print(soma) // 55
```

## Condicionais

No material anterior, vimos sobre `if-else if-else`, além do operador ternário. Agora vamos ver sobre um outro controle de fluxo envolvendo condicionais, o `switch`.

### Switch

O comando switch executa um código diferente dependendo do valor de uma variável ou constante. Veja um exemplo abaixo:

```swift
let numero = 10
switch numero {
    case 0:
        print("Zero")
    default:
        print("Não é zero")
}
```

No `switch`, o comando `default` executa sempre quando os casos não forem satisfeitos.

Se você não quer que nada aconteça quando executar o `default`, você pode colocar o comando `break`, veja abaixo:

```swift
let numero = 10
switch numero {
    case 0:
        print("Zero")
    default: break
}
```

Podemos também brincar com intervalos, como eu mencionei anteriormente:

```swift
let numero = 10
switch numero {
    case 0..<10:
        print("Entre 0 e 9")
    case 10..<20:
        print("Entre 10 e 19") // será printado esse
    default: print("Maior que 20")
}
```

Note que no código acima temos mais de um `case`, o que é totalmente normal.

No próximo exemplo, vamos criar um caso com múltiplos valores usando string:

```swift
let string = "Dog"
switch string {
    case "Dog", "Cat":
        print("Animal doméstico")
    default: print("Animal selvagem")
}
```

Lembrando que quando temos mais de um caso verdadeiro, o primeiro deles será executado.

Uma outra funcionalidade muito interessante desse comando `switch` é o fato de podermos criar condicionais dentro de cada caso. Veja um exemplo abaixo:

```swift
let numero = 4
switch numero {
    case let x where x % 2 == 0: print("Número par")
    default: print("Número ímpar")
}
```

O caso só vai ser executado se certa condição for verdadeira. A parte do `let` faz com que haja uma ligação de uma nova variável com a variável `numero`, que é a variável em que estamos trabalhando no `switch`, enquanto a parte do `where` exibe uma condição.

Essa funcionalidade é chamada de **pattern matching**, ou combinação de padrões.

Porém, veja que nesse caso não estamos usando a variável `x` em momento algum, portanto podemos fazer de uma maneira diferente:

```swift
let numero = 4
switch numero {
    case let _ where numero % 2 == 0: print("Número par")
    default: print("Número ímpar")
}
```

### Extra: gerando números aleatórios

Agora que você já entendeu como usar intervalo de números, uma funcionalidade que você possa querer é gerar um número aleatório. Para isso, usamos intervalo:

```swift
let numeroAleatorio = Int.random(in: 1...10)
```

Nesse caso, vamos gerar um número aleatório entre 1 e 10, incluindo o 10.

Ir para a próxima página: [Funções](06-funcoes.md)