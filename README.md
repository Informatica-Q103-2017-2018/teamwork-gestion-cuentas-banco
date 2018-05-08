# teamwork-gestion-cuentas-banco
teamwork-gestion-cuentas-banco created by GitHub Classroom

#include<stdio.h>

void compra(int acciones, int cantidad);
void venta(int acciones, int cantidad);

void main()
{
  int acciones=15;
  int cantidad;
  int opcion;
  
  printf("1. Compra de acciones.\n
          2. Venta de acciones .\n
          3. Salir.\n");
     
  scanf ("%d",&opcion);
  switch(opcion)
  {
    case 1:
            printf("Numero de acciones que desea comprar");
            scanf(%d,&cantidad);
            compra(acciones,cantidad);
            break;
    
    case 2:
            printf("Numero de acciones que desea vender");
            scanf(%d,&cantidad);
            venta(acciones,cantidad);
            break;
            
    case 3:
            return;
            
    default:
            printf("Opcion invalida");
            
   }
}

void compra(int acciones, int cantidad)
{
    acciones+=cantidad;
    printf("Su numero de acciones actual es: %d\n", acciones);
  }
  
  void venta(int acciones, int cantidad)
      
    
            
          
