# 01 — Introdução ao Swift

## O que é Swift
Swift é a linguagem criada pela Apple em 2014 para desenvolver apps para iPhone, iPad, Mac, Apple Watch, Apple TV e Apple Vision Pro. Desde 2015 é código aberto e também roda em Linux e Windows.

Por que é uma boa primeira linguagem:
- **Segura:** o compilador aponta muitos erros antes de o programa rodar.
- **Legível:** a sintaxe é limpa e lembra frases em inglês.
- **Moderna e rápida:** usada em produção pela Apple e por milhares de empresas.

## O que você vai precisar

| Situação | Ferramenta | Serve para |
|---|---|---|
| Tem Mac | Xcode (grátis na App Store) | Linguagem + apps iOS |
| Tem iPad ou Mac | Swift Playgrounds | Aprender praticando + apps simples |
| Não tem Mac | Swift para Windows/Linux ou SwiftFiddle (navegador) | Só a linguagem |

> Para criar e rodar apps iOS no simulador ou no iPhone, você precisa de um Mac com Xcode. Os módulos 01 a 03 (exceto os trechos de SwiftUI) funcionam em qualquer opção.

## Primeiro programa

```swift
print("Olá, mundo!")
```

**No Xcode:**
1. Abra o Xcode → **File > New > Playground** → modelo **Blank**.
2. Apague o conteúdo, digite o código acima e clique em ▶ (Run).
3. O resultado aparece no console, na parte de baixo.

**No navegador:** abra o SwiftFiddle, cole o código e clique em **Run**.

## Comentários
Comentários são ignorados pelo computador e servem para explicar o código.

```swift
// comentário de uma linha

/* comentário
   de várias linhas */
```

## Do código ao app
1. Você escreve código Swift.
2. O **compilador** transforma o código em um programa.
3. O **Xcode** empacota o programa como app.
4. O app roda no **simulador** ou em um iPhone de verdade.

## Resumo
- Swift é a linguagem oficial para apps da Apple.
- Xcode é a ferramenta principal; há alternativas para praticar sem Mac.
- `print()` mostra informações no console.

➡️ Próximo: [02 — Conceitos fundamentais](02-conceitos.md)
