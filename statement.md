# Optional Intro

Um Optional (opicional) em swift é uma enumeração de dois valores. Um valor atribuído de qualquer tipo e nil (null). Ou seja há duas opções, uma atribuída no nil (nulo).

```swift runnable
let declaracaoCurta: Int? = Int("42") //Atenção ao uso do operador "?"

let declaracaoLonga: Optional<Int> = Int("42") //Generics
```

há duas possibilidade some (valor desempacotado) e none (literal nil)

```swift runnable
let num: Int? = Optional.some(42) // O valor 42 foi empacotado
let semNum: Int? = Optional.none // O valor nil foi atribuído

print(semNum == nil) //mostra true
```

Veja que elementos de um dicionário são intricicamente opcionais logo para fazer acesso aos elementos você deve indicá-lo. Se você estiver certo que o elemento do dicionário possui uma chave e valor válidos você pode usar o operador "!" para indicar que tem certeza que o elemento tem um valor válido para some.

```swift runnable
var msgHTTP = 
  [200: "OK",
   403: "Acesso Negado",
   404: "Arquivo Não Encontrado",
   500: "Erro interno no servidor"]

//veja que aqui usamos a ! (exclamação) para forçar o desempacotamento. Só devemos fazer isso se tivermos certeza de que a chave 200 existe e tem um valor.  
print(msgHTTP[200]!)

```

# Optional - Teste antes de atribuir um valor

Melhor seria se fizessemos um teste antes de usar uma variável/objeto para garantir que o valor não é nulo. para isso podemos declarar uma constante

Veja que a constante erro404 só é criada se existir um valor válido (some) para msgHTTP[404]. Isso evita o uso incorreto do "!".

```swift runnable
var msgHTTP = 
  [200: "OK",
   403: "Acesso Negado",
   404: "Arquivo Não Encontrado",
   500: "Erro interno no servidor"]


if let erro404 = msgHTTP[404] {
  print("Msg 404: \(erro404)")
} else {
  print("Msg 404 não encontrada")
} 

//veja que msgHTTP[405] não existe nesse caso
if let erro405 = msgHTTP[405] {
  print("Msg 405: \(erro405)")
} else {
  print("Msg 405 não encontrada")
}

```

IMPORTANTE: Isso torna swift bastante robusta, pois garante que se um elemento for acessado sem existir o códigio não quebra.

# Optional - Acesso Seguro 

O operador ? também serve para fazer acesso seguro seguro a métodos 

```swift runnable
var msgHTTP = 
  [200: "OK",
   403: "Acesso Negado",
   404: "Arquivo Não Encontrado",
   500: "Erro interno no servidor"]


if msgHTTP[500]?.hasSuffix("servidor") == true {
    print("sufixo servidor encontrado em msgHTTP[500]")
} else {
  print ("msgHTTP[500] não existe")
}

//Repare que o ? também ajuda o código a não parar em caso de um elemento inexistente (key=333 não existe) 
if msgHTTP[333]?.hasSuffix("servidor") == true {
    print("sufixo servidor encontrado em msgHTTP[333]")
} else {
  print ("msgHTTP[333] não existe")
}
```

# Optional - Coalescing 

Use o operador "??"" (Coalescing) para atribuir um valor defeult ao opcional 

```swift runnable

var msgHTTP = 
  [200: "OK",
   403: "Acesso Negado",
   404: "Arquivo Não Encontrado",
   500: "Erro interno no servidor"]


let msgDefaut = "Erro desconhecido"
let msgErro = msgHTTP[333] ?? msgDefaut

// no caso msgHTTP[333] não existe logo msgErro=msgDefaut
print(msgErro)

//Lembrando que usar o ! deve ser evitado pois de nada adianta mandar desempacotar um opcional nil. 

//O compilador reclama (warning)
//print (msgHTTP[500])

//aqui tudo bem, mas perigoso
print (msgHTTP[500]!)

//assim é melhor 
if let msg = msgHTTP[500] {
  print(msg)
}

///O compilador reclama (warning) e nesse caso está sendo feito acesso a um elemento inexistente
//print (msgHTTP[333])

