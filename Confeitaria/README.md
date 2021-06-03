## Exercício Linguagem C - "Confeitaria" 🧁

Eis o enunciado da questão:

*Uma confeitaria está vendendo doces seguindo a tabela de preços dada abaixo. Faça o **ALGORITMO** e o **PROGRAMA EM LINGUAGEM C** para ler o tipo e a quantidade (em Kg) de doce que cada cliente comprou. Calcule e mostre o valor a ser pago pelo cliente por doce comprado e o total da compra realizada. Sabe-se que o cliente poderá comprar vários tipos de doce escolhendo o tipo pelo número indicado na tabela. Sabe-se também que naquele dia foram realizadas 25 vendas. Para cada compra mostre o tipo e os doces comprados por cada cliente, o valor pago por quilo e o total pago por cada cliente.*

Tipo | Doce |Até 5kg |Acima de 5kg
:-----:|:-------:|:----------:|:-----------------:
1 | Trufa |R$ 25.00 por kg |R$ 22.00 por kg
2 | Torta |R$ 24.45 por kg |R$ 22.25 por kg
3 | Bolo |R$ 35.00 por kg |R$ 30.00 por kg

##### Pontos importantes da lógica:

* A entrada de dados se dá pela leitura do **tipo** e **quantidade**;

* Será necessária uma **estrutura de decisão** para o tipo e outra para o preço de acordo com a quantidade;

* Isso se repetirá por 25 vezes, já que são 25 vendas. Portanto, usaremos uma estrutura de repetição com **variável de controle**;

* Além disso, o cliente pode escolher mais de um tipo de doce, então, dentro da repetição com variável de controle, teremos uma repetição com teste **no final**, já que o cliente pode optar por não adicionar mais.

* Por fim, teremos uma série de condicionais compostas encaixadas para que a saída de dados seja **específica** para o cliente, mostrando apenas o que comprou, os quilos comprados, o valor por doce e o valor final.

  ##### Algoritmo:

  ##### Programa:

  ```c
  #include <stdio.h>
  #include <stdlib.h>
  int main()
  {
  	//declaração das variáveis
  	char addTipo;
  	int tipo, contador;
  	float quilosTrufa, quilosTorta, quilosBolo,precoTrufa, precoTorta, precoBolo, quilosScan, precoFinal;
  	//estrutura de repetição com variável de controle
  	for(contador=1; contador<=25; contador ++)//contador <= 25 pois foram realizadas 25 vendas.
  	{
  		//inicializando variáveis para que não haja lixo de memória 
  		//ou sobreposição de valores durante o processo.
  		precoTrufa = 0.0;
  		precoTorta = 0.0;
  		precoBolo = 0.0;
  		quilosTrufa = 0.0;
  		quilosTorta = 0.0;
  		quilosBolo = 0.0;
  		do{
  			printf("(1)Trufa\n(2)Torta\n(3)Bolo\nDigite o tipo de doce que deseja comprar: ");
  			scanf("%d", &tipo);
  			//estrutura de decisão encaixada (switch(case) + composta)
  			switch(tipo)
  			{
  			case 1:
  				printf("Digite a quantidade em quilos que deseja comprar: ");
  				scanf("%f", &quilosScan);
  				quilosTrufa = quilosScan+quilosTrufa; 
  				//obs: torna-se necessário utilizar a variável quilosScan 
  				//para que o cliente possa adicionar mais quilos do mesmo tipo de doce,
  				// somando os valores a cada adição e mostrando ao final o preço real de seu pedido
  				if(quilosTrufa<=5.0)
  				{
  					precoTrufa = quilosTrufa * 25.0;
  				}
  				else
  				{
  					precoTrufa = quilosTrufa * 22.0;
  				}
  				printf("Deseja comprar outro tipo de doce? (S/N): ");
  				fflush(stdin);
  				addTipo = getchar();
  				break;
  			case 2:
  				printf("Digite a quantidade em quilos que deseja comprar: ");
  				scanf("%f", &quilosScan);
  				quilosTorta=quilosScan+quilosTorta;
  				if(quilosTorta<=5.0)
  				{
  					precoTorta = quilosTorta * 24.5;
  				}
  				else
  				{
  					precoTorta = quilosTorta * 22.25;
  				}
  				printf("Deseja comprar outro tipo de doce? (S/N): ");
  				fflush(stdin);
  				addTipo = getchar();
  				break;
  			case 3:
  				printf("Digite a quantidade em quilos que deseja comprar: ");
  				scanf("%f", &quilosScan);
  				quilosBolo=quilosScan+quilosBolo;
  				if(quilosBolo<=5.0)
  				{
  					precoBolo = quilosBolo * 35.0;
  				}
  				else
  				{
  					precoBolo = quilosBolo * 30.0;
  				}
  				printf("Deseja comprar outro tipo de doce? (S/N): ");
  				fflush(stdin);
  				addTipo = getchar();
  				break;
  			default:
  				printf("\n\nDigite um tipo de doce valido\n\n");
  				system("pause");
  				addTipo = 'S';
  				break;
  			}
  		}while (addTipo == 's' || addTipo == 'S');
  		
  		precoFinal = precoTrufa + precoTorta + precoBolo;
  		system("cls");
  		//condicionais que determinarão qual será a saída de dados, 
  		//especificando os tipos, quilos e preço do pedido do cliente
  		if(precoTrufa > 0.0 && precoTorta > 0.0 && precoBolo > 0.0)
  		{
  			printf("-------------------------------------------------------------------");
  			printf("\n\n Compras - Cliente %d\n\n Qtd de Trufa:%.2fKg - Valor:%.2f reais\n\n Qtd de Torta:%.2fKg - Valor:%.2f reais\n\n Qtd de Bolo:%.2fKg - Valor:%.2f reais\n\n Valor total a ser pago: %.2f reais\n\n", contador, quilosTrufa, precoTrufa, quilosTorta, precoTorta, quilosBolo, precoBolo, precoFinal);
  			printf("-------------------------------------------------------------------\n");
  			system("pause");
  			system("cls");
  		}
  		else
  		{
  			if(precoTrufa > 0.0 && precoTorta > 0.0)
  			{
  				printf("-------------------------------------------------------------------");	  		
  				printf("\n\n Compras - Cliente %d\n\n Qtd de Trufa:%.2fKg - Valor:%.2f reais\n\n Qtd de Torta:%.2fKg - Valor:%.2f reais\n\n Valor total a ser pago: %.2f reais\n\n", contador, quilosTrufa, precoTrufa, quilosTorta, precoTorta, precoFinal);	
  				printf("-------------------------------------------------------------------\n");
  				system("pause");
  				system("cls");
  			}
  			else
  			{
  				if(precoTrufa > 0.0 && precoBolo > 0.0)
  				{
  					printf("-------------------------------------------------------------------");
  					printf("\n\n Compras - Cliente %d\n\n Qtd de Trufa:%.2fKg - Valor:%.2f reais\n\n Qtd de Bolo:%.2fKg - Valor:%.2f reais\n\n Valor total a ser pago: %.2f reais\n\n", contador, quilosTrufa, precoTrufa, quilosBolo, precoBolo, precoFinal);
  					printf("-------------------------------------------------------------------\n");
  					system("pause");
  					system("cls");
  				}
  				else
  				{	if(precoTorta >0.0 && precoBolo >0.0)
  					{
  						printf("-------------------------------------------------------------------");
  						printf("\n\n Compras - Cliente %d\n\n Qtd de Torta:%.2fKg - Valor:%.2f reais\n\n Qtd de Bolo:%.2fKg - Valor:%.2f reais\n\n Valor total a ser pago: %.2f reais\n\n", contador, quilosTorta, precoTorta, quilosBolo, precoBolo, precoFinal);
  						printf("-------------------------------------------------------------------\n");
  						system("pause");
  						system("cls");	
  					}
  					else{
  						if(precoTorta==0.0 && precoBolo==0.0 )
  						{
  							printf("-------------------------------------------------------------------");
  							printf("\n\n Compras - Cliente %d\n\n Qtd de Trufa:%.2fKg - Valor:%.2f reais\n\n Valor total a ser pago: %.2f reais\n\n", contador, quilosTrufa, precoTrufa, precoFinal);
  							printf("-------------------------------------------------------------------\n");
  							system("pause");
  							system("cls");	
  						}
  						else{
  							if(precoTrufa==0.0 && precoBolo==0.0)
  							{
  							printf("-------------------------------------------------------------------");
  							printf("\n\n Compras - Cliente %d\n\n Qtd de Torta:%.2fKg - Valor:%.2f reais\n\n Valor total a ser pago: %.2f reais\n\n", contador, quilosTorta, precoTorta, precoFinal);
  							printf("-------------------------------------------------------------------\n");
  							system("pause");
  							system("cls");									
  							}
  							else{
  							printf("-------------------------------------------------------------------");
  							printf("\n\n Compras - Cliente %d\n\n Qtd de Bolo:%.2fKg - Valor:%.2f reais\n\n Valor total a ser pago: %.2f reais\n\n", contador, quilosBolo, precoBolo, precoFinal);
  							printf("-------------------------------------------------------------------\n");
  							system("pause");
  							system("cls");									
  							}
  						}
  					}
  				
  				}
  			}	
  		}
  	}
  	return 0;
  }
  ```

  

  