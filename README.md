# 💰 Sistema Bancário em Python

Este projeto foi desenvolvido como parte de um desafio da plataforma [DIO.me](https://www.dio.me/), com o objetivo de simular as operações básicas de um sistema bancário: **depósito**, **saque** e **extrato**.

---

## 📋 Requisitos do Projeto

O sistema deve:

- ✅ Permitir **depósitos** de valores positivos.
- ✅ Permitir **saques** com as seguintes restrições:
  - Limite de **3 saques diários**.
  - Limite de **R$ 500,00 por saque**.
  - O saque não pode ser realizado caso o saldo seja insuficiente.
- ✅ Exibir um **extrato** com todas as movimentações realizadas (depósitos e saques) e o saldo atual.
- ✅ Ser executado em **linha de comando**, com um **menu interativo**.

---

## 🔧 Tecnologias Utilizadas

- Linguagem: **Python 3.10+**
- Ambiente: **Terminal / Prompt de Comando**

---

## ▶️ Como Executar

1. Clone este repositório:
   ```bash
   git clone https://github.com/seu-usuario/sistema-bancario-python.git
   cd sistema-bancario-python
   ```

2. Execute o script:
   ```bash
   python sistema_bancario.py
   ```

---

## 📑 Menu de Operações

```text
[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair
```

---

## 💻 Código-Fonte

```python
menu = """
[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:
    opcao = input(menu)

    if opcao == "d":
        valor = float(input("Informe o valor do depósito: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"
        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == "s":
        valor = float(input("Informe o valor do saque: "))

        excedeu_saldo = valor > saldo
        excedeu_limite = valor > limite
        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Operação falhou! Você não tem saldo suficiente.")
        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite.")
        elif excedeu_saques:
            print("Operação falhou! Número máximo de saques excedido.")
        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1
        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == "e":
        print("\n================ EXTRATO ================")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")

    elif opcao == "q":
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")
```

---

## ✅ Conclusão

Este projeto representa a primeira versão de um sistema bancário, com operações básicas e regras de negócio implementadas. Foi uma ótima oportunidade para aplicar lógica de programação, estruturas condicionais e laços de repetição com **Python**.

---


