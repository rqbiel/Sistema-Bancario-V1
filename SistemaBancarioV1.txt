menu = """

[d] Depósito
[s] Saque
[e] Extrato
[q] Sair

"""
depositos = []
saques = []
saldo_em_conta = 0
LIMITE_SAQUE = 0
LIMITE_VALOR_SAQUE = 500.00

opcao = 'g'

while opcao != 'q':
    
    opcao = input(menu)

    match opcao:
        case 'd':
            print("Depósito")
            valor_deposito = float(input("Digite o valor do depósito: \n"))
            if valor_deposito > 0:
                print(f"Depósito efetuado no valor de R$ {valor_deposito:.2f}")
                depositos.append(valor_deposito) #cria uma lista com x1,x2,x3,x4...
            else: 
                 print("Valor insuficiente. Por favor, insira um valor positivo!")
            
        case 's':
            print("Saque")
            if LIMITE_SAQUE >= 3:
                print("Limite diário de saques atingido. Volte amanhã!")
                
            else:
                valor_saque = float(input("Digite o valor do saque: \n"))
                if valor_saque > LIMITE_VALOR_SAQUE:
                    print(f"Valor máximo permitido para saque é R$ {LIMITE_VALOR_SAQUE:.2f}")
                elif valor_saque < saldo_em_conta:
                    print(f"Saque efetuado no valor de R$ {valor_saque:.2f}")
                    saques.append(valor_saque) #cria uma lista com x1,x2,x3,x4...
                    LIMITE_SAQUE += 1
                else:
                    print("Não será possível efetuar o saque por falta de saldo\n")
                
            
        case 'e':
            print("Extrato")
            
            for valor in depositos: #for para mostrar todos os valores que foram incluídos na lista "depositos", sem precisar colocar 1 a 1.
                print("Depósito realizado na conta:", valor)            
            
            for valor2 in saques:
                print("Saque realizado na conta:", valor2)
            
            saldo_em_conta = sum(depositos) - sum(saques) #soma todos os valores presentes na lista "Depositos"
            print(f"Saldo em conta: R$ {saldo_em_conta:.2f}")
            
            
            
        case 'q':
            print("Encerrando sistema bancário...")