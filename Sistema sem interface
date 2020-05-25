# -*- coding: utf-8 -*-
# -*- coding: 1252 -*-
import pandas as pd
import csv
import os
import sys
#____________________Listas de Produtos_________
def listas(Produto):
  if Produto == 0:
     Status = ['Pago','Devendo','Fazendo']
     SalgadosList = '[ 0 ]Coxinha \n[ 1 ]Pastel \n[ 2 ]Espetinho'
     Salgados = ['Coxinha','Pastel','Espetinho']
     Valor = [6,4.50,8]
     return SalgadosList, Salgados, Valor, Status
  
  elif Produto == 1:
     DocesList = '[ 0 ]Pudim \n[ 1 ]Arroz Doce \n[ 2 ]Sorvete'
     Doces = ['Pudim','Arroz Doce','Sorvete']
     Valor02 = [7,3,9]
     return DocesList, Doces, Valor02

def receita(UserSearch):
    if UserSearch == 1:
        print(' '*30,'Pago:  R$:',Histórico.loc[Histórico['Status']== 'Pago']['Valor'].sum())
        print(' '*30, 'Devendo: R$:',Histórico.loc[Histórico['Status']== 'Devendo']['Valor'].sum())
        print(' '*30, 'Fazendo: R$:',len(Histórico.loc[Histórico['Status']== 'Fazendo']))
    
    else:
        User = Histórico.loc[Histórico['Nome']=='Denis']
        print(' '*40,'Pago:  R$:',User.loc[User['Status']== 'Pago']['Valor'].sum())
        print(' '*40, 'Devendo: R$:',User.loc[User['Status']== 'Devendo']['Valor'].sum())
        print(' '*40, 'Fazendo:',len(User.loc[User['Status']== 'Fazendo']))
        
Continuar = 'S'
while Continuar == 'S':
  Arquivo = open('C:/Historico/Historico.csv','a',newline="")
  #____________________Menu________________________ 
  print('''Opções
  [ 0 ] Adicionar
  [ 1 ] Histórico
  [ 2 ] Sair''')
  Menu = int(input('>'))
  if Menu == 0:
      print('[ 0 ]Salgados \n[ 1 ]Doces')
      Opcao = int(input('Opções: '))
      print(listas(Opcao)[0])
      Comer = int(input('Produto: '))
      Qtd = int(input('Qtd:  '))
      Nome = str(input('Nome: '))
      print('[ 0 ]Pago \n[ 1 ] Devendo [ 2 ] Fazendo')
      Status = int(input('Status:  '))
      writer = csv.writer(Arquivo,delimiter=',')
      writer.writerow([Nome, listas(Opcao)[1][Comer], Qtd, listas(Opcao)[2][Comer]*Qtd,listas(0)[3][Status]])
  elif Menu == 1:
      Histórico = pd.read_csv('C:\Historico\Historico.csv')
      print(Histórico)
      receita(1)
      Pesquisar = str(input('Buscar Nome: ')).strip().title()
      if Pesquisar != '':
        print(Histórico.loc[Histórico['Nome']== Pesquisar])
        receita(2)
        print(' \n [ 0 ]Pago [ 1 ] Devendo [ 2 ] Fazendo')
        Novo = input('Novo Status: ')
        if Novo.isnumeric():
          for linhas in range(0,len(Histórico)):
              PesquisarLinha  = Histórico['Nome'][linhas] == Pesquisar
              if PesquisarLinha == True:
                 Alteracao = Histórico.iloc[linhas, 4] = listas(0)[3][int(Novo)]
                 Histórico.to_csv('C:/Historico/Historico.csv', index = False)
      Continuar = str(input('Deseja Continuar? S/N \n > ')).capitalize()
      Clear = lambda: os.system('cls')
      Arquivo.close()
      Clear()
  if Menu == 2:
     sys.exit()
