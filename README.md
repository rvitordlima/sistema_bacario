# sistema_bacario
depositos = []
saques = []
i = 0
desejo = 1
operacao = 1

while operacao:
    #Apresentar um menu que contenha 3 opções, depósito, saque e extrato
    print('Depósito = d')
    print('Saque = s')
    print('Extrato = e')
    menu = input('Digite a letra da opção desejada do menu apresentado acima: ')
    if menu == 'd':
        while desejo:
            deposito = float(input('Qual o valor do depósito? '))
            if deposito > 0:
                print('Depósito válido!')
            else:
                print('Depóstio inválido, digite um valor positivo!')

    #Armazenar os depósitos em uma variável para depois ser exibido no extrato
            if deposito > 0:
                depositos.append(deposito)
            desejo = int(input('Gostaria de realizar mais algum depósito? (0 - não ; 1 - sim)  '))
    
    #Saque: permitir 3 saques com limite máximo de R$500,00 cada
    if menu == 's':
        while i < 3:
            saque = float(input('Qual o valor do saque? '))

            if saque > 500:
                print("Limite de saque excedido!")    
            
            i += 1

    #Armazenar todos os saques em uma variável para depois ser exibido no extrato.
            if saque <= 500:
                saques.append(saque)    
            
    #Caso não tenha saldo em conta, mostrar saldo insuficiente 
            if saque > sum(depositos):
                print('Saldo insuficiente para saque!')
 
    #Extrato: tem a lista dos depósitos e dos saques.
    if menu == 'e':
        print(f'Os depósitos foram {depositos} e os saques foram {saques}')
    
    #No final da lista deve exibir o saldo atual (R$xxx,xx)
        saldo = sum(depositos) - sum(saques)
        print(f'O saldo atual é R${saldo}')
    
#Retornar ao menu de opções
    operacao = int(input('Você deseja realizar outra operação? 0 - não ; 1 - sim  '))
