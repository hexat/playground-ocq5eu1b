# Optional Intro

Um Optional (opicional) em swift é uma enumeração de dois valores. Um valor atribuído de qualquer tipo e nil (null). Ou seja há duas opções, uma atribuída no nil (nulo).

```swift runnable
let declaracaoCurta: Int? = Int("42") //uso da ?
let declaracaoLonga: Optional<Int> = Int("42") //Generics
```

# Optional Intro II

há duas possibilidade some (valor desempacotado) e none (literal nil)

```swift runnable
let num: Int? = Optional.some(42) // O valor 42 foi empacotado
let semNum: Int? = Optional.none // O valor nil foi atribuído

print(semNum == nil) //mostra true
```

# Optional Intro III

Veja que elementos de um dicionários são intricicamente opcionais logo para fazer acesso aos elementos você deve desempacota-lo

```swift runnable
var msgHTTP = 
  [200: "OK",
   403: "Acesso Negado",
   404: "Arquivo Não Encontrado",
   500: "Erro interno no servidor"]
```

veja que aqui usamos a ! (exclamação) para forçar o desempacotamento. Só devemos fazer isso se tivermos certeza de que a chave 200 existe e tem um valor  

```swift runnable
print(msgHTTP[200]!) 
```