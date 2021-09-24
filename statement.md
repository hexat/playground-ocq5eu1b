# Optional Intro

Um Optional (opicional) em swift é uma enumeração de dois valores. Um valor atribuído de qualquer tipo e nil (null). Ou seja há duas opções, uma atribuída no nil (nulo).

```swift runnable
let declaracaoCurta: Int? = Int("42") //uso da ?
let declaracaoLonga: Optional<Int> = Int("42") //Generics
```

# Optional Intro

há duas possibilidade some (valor desempacotado) e none (literal nil)

let num: Int? = Optional.some(42) // O valor 42 foi empacotado
let semNum: Int? = Optional.none // O valor nil foi atribuído

print(semNum == nil) //mostra true


