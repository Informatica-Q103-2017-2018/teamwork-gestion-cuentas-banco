#include<stdio.h>
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
	cliente banco[DIM], *punt= &cliente;
	int orden,acciones=15,cantidad,opcion,codigo,i;
  	float apunte;
  	FILE*pf;
	inicializa_cuenta (cliente);


	
	do
	{
	

		printf ("Introduzca la clave de acceso:");
		gets (palabra);
		
		orden = strcmp (clave,palabra);
		
		if (orden!=0)
		{ 
				printf ("\nLa clave introducida es INCORRECTA\n");
				printf ("Vuelva a intentarlo\n\n");
	
		}
	
		if (orden==0)
		{
		printf ("\nLa clave introducida es CORRECTA\n\n");
		pf = fopen("banco.txt", "w+"); 
		if (pf == NULL) 
		{ printf("Error al abrir el fichero.\n"); 
		return -1; } 
		else 
		{ 
		 
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
	            banco[codigo].saldo+=apunte;
	            printf ("\nLa cuenta %i esta actualizada\n",banco[codigo].num_cuenta);
	            printf ("El nuevo saldo es %.2f\n",banco[codigo].saldo);
	            compra(acciones,cantidad);
	            banco[codigo].num_acciones=acciones; 
	               
	            break;
	    
	    	case 2:
	    		printf("Codigo usuario ? <De 0 a %i>",DIM-1);
	            scanf("%d",&codigo);
	            printf("Su numero de acciones actual es: %d\n", acciones);
	            printf("Numero de acciones que desea vender:");
	            scanf("%d",&cantidad);
	           	apunte=cantidad *5.0;
	            banco[codigo].saldo-=apunte;
	            printf ("\nLa cuenta %i esta actualizada\n",banco[codigo].num_cuenta);
	            printf ("El nuevo saldo es %.2f\n",banco[codigo].saldo);
	            venta(acciones,cantidad);
	            banco[codigo].num_acciones=acciones;   
	            break;
	            
	    	case 3:
	            return;
	            
	    	default:
	            printf("Opcion invalida");
	    }
	     
		}
	}
   }while (orden !=0);
	fprintf(pf, "%d\t %d\t %.2f\t", banco[codigo].num_cuenta,banco[codigo].num_acciones, banco[codigo].saldo);
	fclose(pf); 
}

void inicializa_cuenta (struct cliente *punt)
{
	int i;
	
	for (i=0;i<DIM;i++,punt++)
	{
		punt->num_cuenta = (2700+i);
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
      
    
            
          
