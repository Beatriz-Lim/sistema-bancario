# sistema-bancario

menu = f'''
------opções------
[1] Depositar
[2] Sacar
[3] Extrato
[0] sair
------------------
'''

saldo = 0
limite = 500
extrato = ''
numero_saque = 0
LIMITE_SAQUE = 3

while True:
    opcao = int(input(menu))

    if opcao == 1:
        deposito = float(input('Digite o valor a ser depositado: R$'))

        if deposito > 0:
            saldo += deposito
            extrato += f'Depósito: R$ {deposito:.2f}\n'

        else:
            print('Erro na operação! O valor informado é inválido.')

    elif opcao == 2:
        saque = float(input('Digite o valor que deseja sacar: R$'))
        numero_saque += 1
        if numero_saque > LIMITE_SAQUE:
            print('Limite de três saques diarios atingido\nTente novamente amanhã.')

        if saque > 0 and saque <= 500 and saque <= saldo and numero_saque <= 31:
            print('saque realizado com sucesso.')
            saldo -= saque
            extrato += f'Saque: R$ {saque:.2f}\n'

        elif saque > saldo:
            print('Saldo insuficiente.')

        elif saque > 500:
            print('valor de saque excedido.\nATENÇAO! O valor permitido por saque é de R$500,00')

        else:
            print('Erro na operação! O valor informado é inválido.')

    elif opcao == 3:
        print('==========Extrato==========')
        print('Não foram realizadas operações.' if not extrato else extrato)
        print(f'\nSaldo: R$ {saldo:.2f}')
        print(27 * '=')

    elif opcao == 0:
        break

    else:
        print('Operação inválida, Por favor selecione novamente a operação desejada.')
