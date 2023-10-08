# appbank
menu = """

[1] Extrato
[2] Desposito
[3] Saque
[0] Sair

=> """

saldo = 0
limite = 1500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 5

while True:

    opcao = input(menu)

    if opcao == '1':
        print('\n========= EXTRATO ========')
        print('Não foram realizados movimentações.' if not extrato else extrato)
        print(f'\nSaldo: R$ {saldo:.2f}')
        print('$$$$$$$$$$$$$$$$$$$$$$$$$$$$')

    elif opcao == '2':
        valor = float(input('Informe o valor de depósito: '))

        if valor > 0:
            saldo += valor
            extrato += f'Depósito: R$ {valor:.2f}\n'

        else:
            print('Operação falhou! Informe o valor desejado')

    elif opcao == '3':
        valor = float(input('Informe o valor para saque: '))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print('ERRO! consultar saldo!')

        elif excedeu_limite:
            print('ERRO! limite inferior ao desejado.')

        elif excedeu_saques:
            print('Atenção! número de saque excedido')
        
        elif valor > 0:
            saldo -= valor
            extrato += f'Saque: R$ {valor:.2f}\n'
            numero_saques += 1

        else:
            print('Erro! Verifique sua operação.')

    elif opcao == '0':
        break

    else:
        print('Operação errada, selecione o que vai fazer!')
