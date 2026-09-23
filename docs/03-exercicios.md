# 03 — Exercícios

Tente resolver antes de abrir a solução. Os exercícios 1 a 7 rodam em qualquer ambiente; o 8 precisa do Xcode ou do Swift Playgrounds.

## 1. Constantes e variáveis
Declare `nome` (constante) e `idade` (variável). Some 1 à idade e imprima: `Meu nome é X e tenho Y anos`.

<details><summary>Ver solução</summary>

```swift
let nome = "Pedro"
var idade = 20
idade += 1
print("Meu nome é \(nome) e tenho \(idade) anos")
```
</details>

## 2. Par ou ímpar
Dado um número inteiro, imprima se ele é par ou ímpar.

<details><summary>Ver solução</summary>

```swift
let numero = 7
if numero % 2 == 0 {
    print("\(numero) é par")
} else {
    print("\(numero) é ímpar")
}
```
</details>

## 3. Média do aluno
Com um array de notas, calcule a média e imprima a situação: ≥ 7 aprovado, ≥ 5 recuperação, abaixo disso reprovado.

<details><summary>Ver solução</summary>

```swift
let notas = [8.0, 6.5, 7.5]
var soma = 0.0
for nota in notas {
    soma += nota
}
let media = soma / Double(notas.count)
print("Média: \(media)")

if media >= 7 {
    print("Aprovado")
} else if media >= 5 {
    print("Recuperação")
} else {
    print("Reprovado")
}
```
</details>

## 4. Tabuada
Use `for-in` para imprimir a tabuada do 7 (de 1 a 10).

<details><summary>Ver solução</summary>

```swift
for i in 1...10 {
    print("7 x \(i) = \(7 * i)")
}
```
</details>

## 5. Optionals
Tente converter `"abc"` e `"25"` para `Int`. Imprima o número quando der certo e uma mensagem de erro quando falhar.

<details><summary>Ver solução</summary>

```swift
let entradas = ["abc", "25"]
for entrada in entradas {
    if let numero = Int(entrada) {
        print("\(entrada) virou o número \(numero)")
    } else {
        print("\(entrada) não é um número válido")
    }
}
```
</details>

## 6. Função com optional
Crie `func maior(_ numeros: [Int]) -> Int?` que retorna o maior número da lista, ou `nil` se ela estiver vazia.

<details><summary>Ver solução</summary>

```swift
func maior(_ numeros: [Int]) -> Int? {
    guard var maiorAteAgora = numeros.first else {
        return nil
    }
    for n in numeros where n > maiorAteAgora {
        maiorAteAgora = n
    }
    return maiorAteAgora
}

if let resultado = maior([3, 9, 2]) {
    print("Maior: \(resultado)")   // Maior: 9
}
print(maior([]) == nil)            // true
```

> Na prática, arrays já têm `numeros.max()`, que faz o mesmo.
</details>

## 7. Struct e carrinho de compras
Crie a struct `Produto` (nome, preço, quantidade) com um método `total()`. Monte um carrinho com dois produtos e imprima o valor total.

<details><summary>Ver solução</summary>

```swift
struct Produto {
    let nome: String
    let preco: Double
    let quantidade: Int

    func total() -> Double {
        preco * Double(quantidade)
    }
}

let carrinho = [
    Produto(nome: "Caderno", preco: 15.0, quantidade: 2),
    Produto(nome: "Caneta", preco: 3.5, quantidade: 4)
]

let totalGeral = carrinho.reduce(0) { $0 + $1.total() }
print("Total: R$ \(totalGeral)")   // Total: R$ 44.0
```
</details>

## 8. App: contador completo (SwiftUI)
Evolua o app do módulo 02: botões **+**, **−** e **Zerar**. O contador não pode ficar negativo.

<details><summary>Ver solução</summary>

```swift
import SwiftUI

struct ContentView: View {
    @State private var contador = 0

    var body: some View {
        VStack(spacing: 16) {
            Text("\(contador)")
                .font(.largeTitle)

            HStack {
                Button("−") { contador -= 1 }
                    .disabled(contador == 0)
                Button("Zerar") { contador = 0 }
                Button("+") { contador += 1 }
            }
            .buttonStyle(.bordered)
        }
        .padding()
    }
}

#Preview {
    ContentView()
}
```
</details>

➡️ Próximo: [04 — Referências](04-referencias.md)
