# Closures

Neste material, vamos aprofundar um pouco mais o conceito de funções avançadas como *closures*, funções como variáveis, passando funções como argumento de outra função, etc.

## O que são closures?

Closures são funções sem nome. Você pode atribuí-la a uma variável e passar adiante como qualquer outro valor.

## Básico de Closures

Closures também podem acessar valores de qualquer variável ou constante em um contexto externo. 

Vamos criar uma variável para armazenar uma closure:

```swift
var soma = { (a: Int, b: Int) -> Int in
    return a + b
}
soma(2, 5) // 7
```

Veja que essa função, a closure, não possui um nome. O que possui um nome é a variável, apenas.

Tudo que vem depois da palavra-chave `in` é o escopo da função, o bloco de código.

Note também que mesmo declarando os parâmetros como `a` e `b`, na hora de passar os argumentos, não usamos nomes externos para os parâmetros, passamos somente os valores.

Existe uma sintaxe ainda mais curta para closures:

```swift
var soma = { (a: Int, b: Int) -> Int in
    a + b // apenas uma linha possui retorno implícito
}
soma(2, 5)
```

Você pode ainda omitir a lista de parâmetros se você quiser, porque o Swift nos permite referenciar cada parâmetro por um número, começando do zero:

```swift
var soma: (Int, Int) -> Int = {
    $0 + $1 // precisamos usar o sinal de $ para referenciar a variável
}
soma(2, 5) // 7
``` 

## Funções como parâmetros

Veja o exemplo abaixo:

```swift
func operarEmNumeros(_ a: Int, _ b : Int, operacao: (Int, Int) -> Int) -> Int {
    return operacao(a, b)
}

var soma = { (_ a: Int, _ b: Int) -> Int in
    return a + b
}

operarEmNumeros(3, 4, operacao: soma)
```

A função `operarEmNumeros` recebe três parâmetros: os dois primeiros são números inteiros, e o terceiro é uma outra função que recebe dois inteiros e retorna um inteiro.

Se você preferir, pode declarar a função no momento em que você a passa para a `operarEmNumeros()`. Veja o exemplo abaixo para ficar mais claro:

```swift
func operarEmNumeros(_ a: Int, _ b : Int, operacao: (Int, Int) -> Int) -> Int {
    return operacao(a, b)
}

operarEmNumeros(3, 4, operacao: { (a: Int, b: Int) -> Int in
    return a + b
})
```

Veja que agora, a função `operacao` está sendo passada diretamente na lista de parâmetros da função `operarEmNumeros()`.

Se a função for o último parâmetro de uma função (como é o caso), podemos usar uma sintax diferente chamada de **trailing closure**:

```swift
func operarEmNumeros(_ a: Int, _ b : Int, operacao: (Int, Int) -> Int) -> Int {
    return operacao(a, b)
}

operarEmNumeros(3, 4) { (a: Int, b: Int) -> Int in
    return a + b
}
```

Isso pode parecer estranho, mas é exatamente o mesmo que o trecho de código anterior, exceto que você removeu o nome da `operacao` e puxou as chaves para fora da lista de parâmetros de chamada da função.

Closures no Swift são muito utilizadas quando falamos sobre métodos assíncronos. 

Eu sei que closures pode parecer bastante confuso no começo, eu também já tive dificuldade. Se tiver alguma dúvida, pode me chamar em alguma das minhas redes sociais pra gente resolver!

Ir para a próxima página: [Iterando sobre coleções com closures](13-iterando-colecoes.md)