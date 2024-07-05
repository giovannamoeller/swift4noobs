# Sets

Sets são muito parecidos com arrays, também são coleções de dados em formato de lista, representados com o uso de colchetes [] e com dados do mesmo tipo.

Porém, as diferenças entre arrays e sets são:
- Enquanto é permitido a repetição de um mesmo valor no array (ele pode aparecer múltiplas vezes), nos sets isso não acontece: um valor aparece uma única vez. 
- A ordem dos elementos dentro de um *set* muda a cada execução do programa. Por esse motivo não conseguimos acessar um elemento pelo seu index, porque os elementos mudam de ordem toda vez.

## Criando um Set

Para criar um Set, precisamos declarar especificamente seu tipo, pois se deixarmos o Swift detectar automaticamente, ele entende que é um Array.

```swift
let primeiroSet: Set<Int> = []
let array = [1, 2, 3, 4] // Array
let setExplicito: Set<Int> = [1, 2, 3, 4]
// ou também podemos declarar assim:
let algumSet = Set([1, 2, 3, 4])
```

Se criarmos um Set com elementos repetidos, ele irá excluir a segunda vez (ou mais vezes) que esse elemento aparece, deixando em apenas uma vez:

```swift
let set: Set<Int> = [1, 2, 3, 4, 1]
// [3, 2, 4, 1] (lembra que a ordem pode mudar a cada execução)
```

## Acessando elementos

Como não há uma ordem definida, não conseguimos acessar via index. Portanto, precisamos usar um método chamado `contains`:

```swift
let set: Set<Int> = [1, 2, 3, 4, 1]
print(set.contains(3))
```

## Adicionando e removendo elementos

Para adicionar, usamos a função `insert()`, enquanto para remover, usamos `remove()`.

```swift
let set: Set<Int> = [1, 2, 3, 4]
set.insert(5)
set.remove(3)
```

Ir para a próxima página: [Tuplas](10-tuplas.md)