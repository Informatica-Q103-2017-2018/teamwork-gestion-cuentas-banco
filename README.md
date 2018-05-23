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
void compra(int acciones, int cantidad); 
void venta(int acciones, int cantidad);


main()
{
	char clave[7]={"ETSIDI"};
	char palabra [7];
	struct cliente usuario [DIM];
	int i=1,orden,acciones=15,cantidad,opcion,codigo;
	float apunte;
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
		
			printf ("Que operacion desea realizar ahora:\n\n");
			printf ("1. Compra de acciones.\n");
		  	printf ("2. Venta de acciones.\n");
		  	printf ("3. Salir.\n");
		  	printf ("\n Opcion:");
		  	scanf ("%d",&opcion);
		  
			  	switch(opcion)
			  	{
			    	case 1:
			    		printf("Codigo usuario ? <De 0 a %i>",DIM-1);
			            scanf("%d",&codigo);
			            printf("Su numero de acciones actual es: %d\n", acciones);
			            printf("Numero de acciones que desea comprar:");
			            scanf("%d",&cantidad);
			           	apunte=cantidad *5.0;
			            usuario[codigo].saldo+=apunte;
			            printf ("\nLa cuenta %i esta actualizada\n",usuario[codigo].num_cuenta);
			            printf ("El nuevo saldo es %.2f\n",usuario[codigo].saldo);
			            compra(acciones,cantidad);
			            usuario[codigo].num_acciones=acciones+cantidad; 
			            break;
			    
			    	case 2:
			    		printf("Codigo usuario ? <De 0 a %i>",DIM-1);
			            scanf("%d",&codigo);
			            printf("Su numero de acciones actual es: %d\n", acciones);
			            printf("Numero de acciones que desea vender:");
			            scanf("%d",&cantidad);
			           	apunte=cantidad *5.0;
			            usuario[codigo].saldo-=apunte;
			            printf ("\nLa cuenta %i esta actualizada\n",usuario[codigo].num_cuenta);
			            printf ("El nuevo saldo es %.2f\n",usuario[codigo].saldo);
			            venta(acciones,cantidad);
			        	usuario[codigo].num_acciones=acciones-cantidad;   
			            break;
			            
			    	case 3:
			            return;
			            
			    	default:
			            printf("Opcion invalida");
		    	}
		     
	}
	
	 
	
	fprintf(pf, "%d\t %d\t %.2f\t", usuario[codigo].num_cuenta,usuario[codigo].num_acciones, usuario[codigo].saldo);
	fclose(pf); 
	
}

void inicializa_cuenta (struct cliente *punt) 
{ 
	int i;

	for (i=0;i<DIM;i++,punt++)
	{
		punt->num_cuenta=(2700+i);
		punt->num_acciones;
		punt->saldo=3000;
	}
}

void compra(int acciones, int cantidad) 
{ 
	acciones+=cantidad; 
	printf("Su numero de acciones actual es: %d\n", acciones);
	
}

void venta(int acciones, int cantidad) 
{ 
	if (acciones<cantidad) 
		printf("No posee suficientes acciones para vender\n"); 
	else 
		acciones-=cantidad; 
		printf("Su numero de acciones actual es: %d\n", acciones); 
}
