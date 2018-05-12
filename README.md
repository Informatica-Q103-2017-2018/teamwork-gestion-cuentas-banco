# teamwork-gestion-cuentas-banco
teamwork-gestion-cuentas-banco created by GitHub Classroom

#include<stdio.h>
#include<string.h>

main()
{
	char clave[7]={"ETSIDI"};
	char palabra [7];
	int orden,intento=1,i;
  	int acciones=15;
  	int cantidad;
  	int opcion;

	do
	{
	
	printf ("Introduzca la contrase?a:");
	gets (palabra);
	
	orden = strcmp (clave,palabra);
	
	if (orden!=0)
	{
	
			printf ("\nLa contrase?a introducida es INCORRECTA\n");
			printf ("Vuelva a intentarlo\n\n");
	}

	
	if (orden==0)
	{
	printf ("\nLa contrase?a introducida es CORRECTA\n\n");
	printf ("Que operacion desea realizar ahora:\n\n");
	
	
	
void compra(int acciones, int cantidad);
void venta(int acciones, int cantidad);

  printf ("1. Compra de acciones.\n");
  printf ("2. Venta de acciones.\n");
  printf ("3. Salir.\n");
  printf ("\n Opcion:");
  scanf ("%d",&opcion);
  
  switch(opcion)
  {
    case 1:
            printf("Numero de acciones que desea comprar:");
            scanf("%d",&cantidad);
            compra(acciones,cantidad); 
            break;
    
    case 2:
            printf("Numero de acciones que desea vender ");
            scanf("%d",&cantidad);
            venta(acciones,cantidad);
            break;
            
    case 3:
            return;
            
    default:
            printf("Opcion invalida");
        }
            
   }
   }while (orden !=0);
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
  
  
  
      
    
            
          
