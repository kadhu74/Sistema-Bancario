# Sistema-Bancario
Criação de um sistema bancário simples

from time import sleep

saldo = 0
extrato = ''
limite = 500
numero_saques = 0
LIMITE_SAQUES = 3

while True:
    print('\n===menu===')
    print('[d] Depositar')
    print('[s] Sacar')
    print('[e] Extrato')
    print('[q] Sair')

    opcao = input('Escolha uma opção: ').lower()

    if opcao == 'd':
        valor = float(input('Informe o valor do Depósito: '))
        if valor > 0:
            saldo += valor
            extrato += f'Depósito: R${valor:.2f}\n'
            print('Depósito realizado com sucesso')
        else:
            print('Operação Falhou!! Valor inválido para depósito')
        sleep(1.5)

    elif opcao == 's':
        valor = float(input('Informe o valor para saque: '))
        excedeu_saldo = valor > saldo
        excedeu_limite = valor > limite
        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print('Operação Falhou!! Você não tem saldo suficiente')
        elif excedeu_limite:
            print('Operação Falhou!! O valor excede o limite de saque')
        elif excedeu_saques:
            print('Operação Falhou!! Número máximo de saques atingido')

        elif valor > 0:
            saldo -= valor
            extrato += f'Saque: R${valor:.2f}\n'
            numero_saques += 1
            print('Saque Realizado com Sucesso!!')

        else:
            print('Operação Falhou!! Informe um valor válido para o saque')
        sleep(1.5)

    elif opcao == 'e':
        print('\n===EXTRATO===')
        print(extrato if extrato else 'Não foram realizadas movimentações')
        print(f'\nSaldo atual: R${saldo:.2f}')
        sleep(2.5)

    elif opcao == 'q':
        print('Muito Obrigado por utilizar nosso Banco!! Fechando o programa')
        sleep(2)
        break

else:
    print('Operação Inválida!! Por favor selecione a opção desejada')
