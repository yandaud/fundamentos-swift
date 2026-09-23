# 02 — Conceitos fundamentais

## 1. Constantes e variáveis

```swift
let nome = "Ana"   // constante: não muda
var idade = 20     // variável: pode mudar
idade = 21
// nome = "Bia"    ❌ erro: 'nome' é constante
```

> Regra prática: use `let` por padrão e `var` só quando o valor precisar mudar.

## 2. Tipos
Swift descobre o tipo sozinho (**inferência**), mas você pode declarar.

```swift
let inteiro: Int = 10
let decimal: Double = 3.14
let texto: String = "Swift"
let ligado: Bool = true
let cidade = "Brasília"   // inferido como String

print("Tenho \(idade) anos")   // interpolação: \(valor) dentro do texto
```

Swift não mistura tipos sem você pedir:

```swift
let a = 5
let b = 2.5
// let soma = a + b      ❌ Int + Double
let soma = Double(a) + b // 7.5
```

## 3. Operadores

| Tipo | Operadores | Exemplo |
|---|---|---|
| Aritméticos | `+ - * / %` | `7 / 2` → `3` (divisão de inteiros), `7 % 2` → `1` |
| Comparação | `== != > < >= <=` | `idade >= 18` |
| Lógicos | `&& \|\| !` | `temIngresso && idade >= 18` |

## 4. Coleções

```swift
// Array: lista ordenada
var frutas = ["maçã", "banana"]
frutas.append("uva")
print(frutas[0])      // maçã
print(frutas.count)   // 3

// Dictionary: pares chave → valor
var notas = ["Ana": 9.5, "Leo": 7.0]
notas["Bia"] = 8.0
print(notas["Ana"] ?? 0)   // 9.5 (a chave pode não existir, por isso o ??)

// Set: sem repetição e sem ordem
let cores: Set = ["azul", "verde", "azul"]
print(cores.count)    // 2
```

## 5. Controle de fluxo

```swift
let nota = 7.5
if nota >= 7 {
    print("Aprovado")
} else if nota >= 5 {
    print("Recuperação")
} else {
    print("Reprovado")
}

let dia = 3
switch dia {
case 1, 7:
    print("Fim de semana")
case 2...6:
    print("Dia útil")
default:
    print("Dia inválido")
}

for fruta in frutas {
    print(fruta)
}

for i in 1...3 {
    print(i)   // 1, 2, 3
}

var contagem = 3
while contagem > 0 {
    print(contagem)
    contagem -= 1
}
```

> No Swift, o `switch` precisa cobrir todos os casos (por isso o `default`) e não "cai" para o próximo `case`.

## 6. Optionals
Um optional (`?`) é um valor que **pode existir ou não** (`nil`). É o que deixa o Swift tão seguro.

```swift
var apelido: String? = nil
apelido = "Pedrinho"

if let apelido {
    print("Apelido: \(apelido)")
} else {
    print("Sem apelido")
}

let numero = Int("42")   // Int? — a conversão pode falhar
print(numero ?? 0)       // ?? define um valor padrão

func saudar(_ nome: String?) {
    guard let nome else {
        print("Nome não informado")
        return
    }
    print("Olá, \(nome)!")
}
```

> Evite o `!` (desembrulho forçado): se o valor for `nil`, o app trava.

## 7. Funções

```swift
func somar(_ a: Int, _ b: Int) -> Int {
    return a + b
}
print(somar(2, 3))   // 5

func cumprimentar(nome: String, saudacao: String = "Olá") -> String {
    "\(saudacao), \(nome)!"
}
print(cumprimentar(nome: "Ana"))                  // Olá, Ana!
print(cumprimentar(nome: "Leo", saudacao: "Oi"))  // Oi, Leo!
```

- `nome:` é o **rótulo** usado na chamada; `_` dispensa o rótulo.
- `= "Olá"` é um valor padrão.
- Funções de uma linha podem omitir o `return`.

## 8. Closures
Closure é uma função sem nome, passada como valor. Aparece muito com coleções.

```swift
let numeros = [1, 2, 3, 4, 5]
let dobrados = numeros.map { $0 * 2 }          // [2, 4, 6, 8, 10]
let pares = numeros.filter { $0 % 2 == 0 }     // [2, 4]
let nomes = ["Leo", "Ana", "Bia"].sorted()     // ["Ana", "Bia", "Leo"]
```

## 9. Structs, classes e enums

```swift
struct Aluno {
    let nome: String
    var nota: Double

    func situacao() -> String {
        nota >= 7 ? "Aprovado" : "Reprovado"
    }
}

class Conta {
    var saldo: Double = 0
    func depositar(_ valor: Double) {
        saldo += valor
    }
}
```

**Diferença principal:** struct é **copiada**; class é **compartilhada**.

```swift
let aluno1 = Aluno(nome: "Ana", nota: 8)
var aluno2 = aluno1
aluno2.nota = 5
print(aluno1.nota)   // 8.0 — cada um tem sua cópia

let conta1 = Conta()
let conta2 = conta1
conta2.depositar(100)
print(conta1.saldo)  // 100.0 — as duas apontam para a mesma conta
```

> Prefira `struct`. O SwiftUI é todo construído com structs.

**Enum** representa um conjunto fechado de opções:

```swift
enum Clima {
    case sol, chuva, nublado
}

let hoje = Clima.chuva
switch hoje {
case .sol:     print("Leve óculos escuros")
case .chuva:   print("Leve guarda-chuva")
case .nublado: print("Leve um casaco")
}
```

## 10. Primeiro app com SwiftUI
SwiftUI é o framework da Apple para montar telas com código Swift.

```swift
import SwiftUI

struct ContentView: View {
    @State private var contador = 0

    var body: some View {
        VStack(spacing: 16) {
            Text("Você tocou \(contador) vezes")
                .font(.title2)
            Button("Tocar") {
                contador += 1
            }
            .buttonStyle(.borderedProminent)
        }
        .padding()
    }
}

#Preview {
    ContentView()
}
```

**Como rodar:** Xcode → **File > New > Project** → **iOS > App** (Interface: SwiftUI) → substitua o conteúdo de `ContentView.swift` → escolha um simulador → ▶.

| Peça | O que faz |
|---|---|
| `View` | Struct que descreve uma tela ou parte dela |
| `body` | O conteúdo que aparece na tela |
| `@State` | Guarda um valor; quando ele muda, a tela é redesenhada |
| `VStack` / `HStack` | Empilha elementos na vertical / horizontal |
| `.font`, `.padding` | Modificadores que ajustam a aparência |

➡️ Próximo: [03 — Exercícios](03-exercicios.md)
