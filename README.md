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
	char clave[7]={"ETSIDI"};
	char palabra [7];
	struct cliente usuario [DIM];
	int i=1,orden,acciones,cantidad,opcion,codigo;
	char opcion2 ='s';
	FILE*pf;
	inicializa_cuenta (usuario);
	
	
	
	while (i<4)
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

	if (i>3)
	{
		printf ("\nACCESO DENEGADO\n\n");		
	}
	
	else
	{
		printf ("\nLa clave introducida es CORRECTA\n\n");
		printf ("ACCESO PERMITIDO\n\n");
		
			pf = fopen("banco.txt", "w+"); 
			if (pf == NULL) 
			{ 	
				printf("Error al abrir el fichero.\n"); 
				return -1;
			}
			
			while (opcion2 =='s')
			{
			
				printf ("Que operacion desea realizar:\n\n");
				printf ("1. Compra de acciones.\n");
			  	printf ("2. Venta de acciones.\n");
			   	printf ("\nOpcion:");
			  	scanf ("%d",&opcion);
			  	
				if (codigo==0 || codigo==1 ||codigo==2 ||codigo==3 ||codigo==4)
				{
					switch(opcion)
				  	{
				    	case 1:
				    		printf("Codigo usuario ? <De 0 a %i>",DIM-1);
							scanf("%d",&codigo);
				            printf("Su numero de acciones actual es: %d\n", usuario[codigo].num_acciones);
				            printf("Numero de acciones que desea comprar:");
				            scanf("%d",&cantidad);
				            compra(usuario[codigo].num_acciones,cantidad);
				            usuario[codigo].num_acciones+=cantidad; 
				            usuario[codigo].saldo-=cantidad*5.0;
				            printf ("\nLa cuenta %i esta actualizada\n",usuario[codigo].num_cuenta);
				            printf ("El nuevo saldo es %.2f\n",usuario[codigo].saldo);
				                   
				            break;
				    
				    	case 2:
				    		printf("Codigo usuario ? <De 0 a %i>",DIM-1);
							scanf("%d",&codigo);
				            printf("Su numero de acciones actual es: %d\n", usuario[codigo].num_acciones);
				            printf("Numero de acciones que desea vender:");
				            scanf("%d",&cantidad);
				            venta(usuario[codigo].num_acciones,cantidad);
				            if (usuario[codigo].num_acciones>cantidad) 
							{
								usuario[codigo].num_acciones-=cantidad; 
								usuario[codigo].saldo+=cantidad*5.0;
							}
				            printf ("\nLa cuenta %i esta actualizada\n",usuario[codigo].num_cuenta);
				            printf ("El nuevo saldo es %.2f\n",usuario[codigo].saldo);
				            
				        	break;
				            
				    	default:
				            printf("Opcion invalida");
				            break;
				
			    	
					}
				
				}
				
				if (codigo!=0 && codigo!=1 && codigo!=2 && codigo!=3 && codigo!=4)
				
				{
				printf("Codigo invalido");	
				}
			
				printf("\nDesea repetir alguna operacion?(s/n)\n");
				printf("Opcion:");
				scanf("%c", &opcion2);
				opcion2 = getchar();
			
			
			}
			    
						while (opcion != 's')
			{
				printf("\n\n");
				printf("Grascias por utilizar este programa\n\n");
				printf ("Hasta pronto!!\n\n");
				break;		
			}

 	 }
	
	
	for(i=0;i<=4;i++)	
	{
		fprintf(pf, "\nCódigo cliente:\t%d\t Número de acciones:\t%d\t Saldo en cuenta:\t%.2f\t\n", usuario[i].num_cuenta,usuario[i].num_acciones, usuario[i].saldo);
	}
	fclose(pf); 
	
}


void inicializa_cuenta (struct cliente *punt) 
{ 
	int i;

	for (i=0;i<DIM;i++,punt++)
	{
		punt->num_cuenta=(2700+i);
		punt->num_acciones=15;
		punt->saldo=3000;
	}
}

void compra(int num_acciones, int cantidad) 
{ 
	num_acciones+=cantidad; 
	printf("\nSu numero de acciones actual es: %d\n",num_acciones);
	
}

void venta(int num_acciones, int cantidad) 
{ 
	
	if (num_acciones<cantidad)
	{
	 	printf("\nNo posee suficientes acciones para vender\n"); 
	 }
	
	else 
	{
		num_acciones-=cantidad; 
		printf("\nSu numero de acciones actual es: %d\n",num_acciones); 
	}
}
		
