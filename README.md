
// Programa que permite la actualizacion de saldo y numero de acciones que poseen los usuarios de un banco. 
// El programa tiene tres intentos para introducir la clave de acceso correctamente.


#include <stdio.h>
#include<string.h>
#define DIM 5


struct cliente  
{ 
	int num_cuenta; 
	int num_acciones; 
	float saldo;

};

void inicializa_cuenta (struct cliente *punt);
void compra(int num_acciones, int cantidad); 
void venta(int num_acciones, int cantidad);


main()
{
	char palabra [7],clave[7]={"ETSIDI"};// Clave de acceso al programa
	struct cliente usuario [DIM];// Vector de la estrcuctura cliente
	int i=1,orden,acciones,cantidad,opcion,codigo;
	char opcion2;
	FILE*pf; // Fichero
	inicializa_cuenta (usuario);//LLamada a la función inicializa_cuenta
	
	
	
	while (i<4) //Acceso al programa mediante clave 
	{
		printf ("Introduzca la clave de acceso:");
		gets (palabra);
		
		orden = strcmp (clave,palabra);
		
		if (orden!=0)
		{
			++i;
			printf ("\nLa clave introducida es INCORRECTA\n\n");
			continue;
			
		}
		
		if (orden==0)
		{
			break;
		}
		
	}

	if (i>3) //Se tienen 3 intentos para introducir la clave correcta. Si no, el programa se cierra
	{
		printf ("\nACCESO DENEGADO\n\n");		
	}
	
	else
	{
		printf ("\nLa clave introducida es CORRECTA\n\n");
		printf ("ACCESO PERMITIDO\n\n");
		
			pf = fopen("banco.txt", "w+"); //Abrimos el fichero 'banco.txt', que si no existe en el ordenador, se crea automaticamente.
			if (pf == NULL) 
			{ 	
				printf("Error al abrir el fichero.\n"); 
				return -1;
			}
			
				
			while (opcion2 =='s'|| opcion2 =='S')
			{
				
				printf ("\nQue operacion desea realizar:\n\n");//Se pide la operación que se quiere realizar
				printf ("1. Compra de acciones.\n");
				printf ("2. Venta de acciones.\n");
				printf ("\nOpcion:");
				scanf ("%d",&opcion);
				printf("\nCodigo usuario ? <De 0 a %i>",DIM-1);//Se pide el código de usuario para abrir las distintas cuentas
				scanf("%d",&codigo);//El número del código será la posición del vector usuario elegido.
					
				if (codigo==0 || codigo==1 || codigo==2 || codigo==3 || codigo==4)//Si el código es válido, se procede a realizar la operación deseada
				{
				
					switch(opcion)
					  	{
					    	case 1:
					    		
								printf("\nSu numero de acciones actual es: %d\n", usuario[codigo].num_acciones);
						        printf("\nNumero de acciones que desea comprar:");
						        scanf("%d",&cantidad);
						        compra(usuario[codigo].num_acciones,cantidad);//LLamada a la funcion compra
						        usuario[codigo].num_acciones+=cantidad; 
						        usuario[codigo].saldo-=cantidad*5.0;// Cada acción cuesta 5 euros
						        printf ("\nLa cuenta %i esta actualizada\n",usuario[codigo].num_cuenta);
						        printf ("El nuevo saldo es %.2f\n",usuario[codigo].saldo);
						        break;
						        	
					        		
					    
					    	case 2:
					    		
						    	printf("\nCodigo usuario ? <De 0 a %i>",DIM-1);
								scanf("%d",&codigo);
								printf("\nSu numero de acciones actual es: %d\n", usuario[codigo].num_acciones);
						        printf("\nNumero de acciones que desea vender:");
						        scanf("%d",&cantidad);
						        venta(usuario[codigo].num_acciones,cantidad);//LLamada a la función venta
						        if (usuario[codigo].num_acciones>cantidad) 
								{
									usuario[codigo].num_acciones-=cantidad; 
									usuario[codigo].saldo+=cantidad*5.0;
								}
						        printf ("\nLa cuenta %i esta actualizada\n",usuario[codigo].num_cuenta);
						        printf ("El nuevo saldo es %.2f\n",usuario[codigo].saldo);
						        break;
						        	
						   	default:
						   		
					            printf("\nOpcion invalida\n");
					            break;
					
				    	
						}
				}
				
				else
				{
					printf ("Codigo invalido\n");// En caso de poner un numero que no sea 0-4 
					break;
				}
			}
						        
			do
			{
				printf("\nDesea repetir alguna operacion?(s/n)\n");//Permite realizar mas operaciones al finalzar la anterior
				printf("Opcion:");
				scanf("%c", &opcion2);
				opcion2 = getchar();
			}while (opcion2 !='s'&& opcion2 !='S');
				
						
			printf("\n\n");
			printf("Gracias por utilizar este programa\n\n");
			printf ("Hasta pronto!!\n\n");
			
				
			
			
	}
				
	
			 
						
	for(i=0;i<=4;i++)//Imprime en el fichero las operaciones realizadas.	
	{
		fprintf(pf, "\nCódigo cliente:\t%d\t Número de acciones:\t%d\t Saldo en cuenta:\t%.2f\t\n", usuario[i].num_cuenta,usuario[i].num_acciones, usuario[i].saldo);
	}
	fclose(pf);//Cerramos el fichero.  
	
}
void inicializa_cuenta (struct cliente *punt)//Inicializa los elementos del vector estructura.
{ 
	int i;

	for (i=0;i<DIM;i++,punt++)
	{
		punt->num_cuenta=(2700+i);
		punt->num_acciones=15;
		punt->saldo=3000;
	}
}

void compra(int num_acciones, int cantidad) // Suma la cantidad de acciones
{ 
	num_acciones+=cantidad; 
	printf("\nSu numero de acciones actual es: %d",num_acciones);
	
}

void venta(int num_acciones, int cantidad) // Suma la cantidad de acciones
{ 
	
	if (num_acciones<cantidad)
	{
	 	printf("\nNo posee suficientes acciones para vender\n"); 
	 }
	
	else 
	{
		num_acciones-=cantidad; 
		printf("\nSu numero de acciones actual es: %d",num_acciones); 
	}
}

