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
        valor = float(input("Qual valor deseja depositar? \n"))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"
            print("Valor depositado!")
        else:
            print("Valor inválido para depósito!")

    elif opcao == "s":
        valor = float(input("Qual valor deseja sacar? \n"))

        excedeu_saldo = valor > saldo
        excedeu_limite = valor > limite
        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Erro! Saldo insuficiente.")

        elif excedeu_limite:
            print(f"Erro! O valor do saque não pode exceder R$ {limite:.2f}.")

        elif excedeu_saques:
            print("Erro! Número máximo de saques atingido.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque:    R$ {valor:.2f}\n"
            numero_saques += 1
            print("Saque realizado com sucesso!")

        else:
            print("Valor inválido para saque!")

    elif opcao == "e":
        print("\n========= EXTRATO =========")
        print("Nenhuma movimentação." if not extrato else extrato)
        print(f"Saldo: R$ {saldo:.2f}")
        print("===========================")

    elif opcao == "q":
        break

    else:
        print("Opção inválida!!")
