#include <iostream>
#include <string>
#include <cstdlib>
#include <stdio.h>

using namespace std;

template <class Tipo,int Maximo>

class Pila{
    int Tope;
    Tipo elementos[Maximo];

public:
    Pila();
    bool Vacia();
    bool Llena();
    bool Insertar(Tipo Valor);
    bool Remover(Tipo &Valor);
    int Contar();
    void Invertir();
};

template <class Tipo, int Maximo>

Pila <Tipo, Maximo>::Pila(){
    Tope=-1;
};

template <class Tipo, int Maximo>
int Pila<Tipo, Maximo>::Contar(){
    return Tope+1;
};

template<class Tipo, int Maximo>
bool Pila<Tipo, Maximo>::Vacia(){
    return Tope==-1;
};

template <class Tipo, int Maximo>
bool Pila<Tipo,Maximo>::Llena(){
    return Tope==Maximo-1;
};

template <class Tipo, int Maximo>
bool Pila<Tipo,Maximo>::Insertar(Tipo Valor){
    if(!Llena()){
        Tope++;
        elementos[Tope]=Valor;
        return true;
    }
    else return false;
};
template <class Tipo, int Maximo>
bool Pila<Tipo,Maximo>::Remover(Tipo &Valor){
    if(!Vacia()){
        Valor=elementos[Tope];
        Tope--;
        return true;
    }
    else return false;
};

template <class Tipo, int Maximo>
void Pila<Tipo, Maximo>::Invertir() {
    int i = 0;
    int j = Tope;
    while (i < j) {
        Tipo Auxiliar = elementos[i];
        elementos[i] = elementos[j];
        elementos[j] = Auxiliar;
        i++;
        j--;
    }
}
string El,Ed,T;
int respe;
int opc=0, resp, j=0, i=-1;

struct Tipoequipos{
    string codigo, Nombre, tipo;
    int cantidad;
    float Precio;
    float descuento;

}Equipos;

Pila <Tipoequipos, 50> Tiquipos;
Pila <Tipoequipos, 50> PilEl;
Pila <Tipoequipos, 50> PilEd;
Pila <Tipoequipos, 50> PilT;
Pila <Tipoequipos, 50> PilaAux;

void CargarPila(Pila <Tipoequipos, 50> &Tiquipos){
    resp=1;
    cout<<"REGISTRANDO DATOS DE LOS EQUIPOS"<<endl;
    while(resp==1){
        i++;
         cout<<endl<<"Ingrese el tipo:"<<endl;        
         cout<<"1).Electronicos"<<endl;
         cout<<"2).Electrodomesticos"<<endl;
         cout<<"3).Telefonicos"<<endl;
         
         cin>>respe;
         switch(respe){        
             case 1:
                           cout<<endl<<"Equipos Electronicos:"<<endl<<endl;
             Equipos.tipo="El";
        cout<<"Ingrese la el codigo:";cin>>Equipos.codigo;
        cout<<"Ingrese el Nombre del Equipo:";cin>>Equipos.Nombre;
        cout<<"Ingrese la cantidad:";cin>>Equipos.cantidad;
        cout<<"Ingrese el precio:";cin>>Equipos.Precio;
                 
                 break;
             case 2:
                            cout<<endl<<"Equipos Electronicos:"<<endl<<endl;
             Equipos.tipo="Ed";
        cout<<"Ingrese la el codigo:";cin>>Equipos.codigo;
        cout<<"Ingrese el Nombre del Equipo:";cin>>Equipos.Nombre;
        cout<<"Ingrese la cantidad:";cin>>Equipos.cantidad;
        cout<<"Ingrese el precio:";cin>>Equipos.Precio;
                 
                 break;
             case 3:
                             cout<<endl<<"Equipos Electronicos:"<<endl<<endl;
             Equipos.tipo="T";
        cout<<"Ingrese la el codigo:";cin>>Equipos.codigo;
        cout<<"Ingrese el Nombre del Equipo:";cin>>Equipos.Nombre;
        cout<<"Ingrese la cantidad:";cin>>Equipos.cantidad;
        cout<<"Ingrese el precio:";cin>>Equipos.Precio;
                          
                 break;
            
         }
       if(!Tiquipos.Llena()){
             Tiquipos.Insertar(Equipos);
         }
         else
             cout<<"No se Puede Insertar"<<endl;
         cout<<"\nQuiere ingresar otro equipo?"<<endl<<"1.Si"<<endl<<"2.No"<<endl;cin>>resp;  
    };
     
         };
void Clasificar(Pila <Tipoequipos, 50> &Tiquipos,Pila <Tipoequipos, 50> &PilEl,Pila <Tipoequipos, 50> &PilEd,Pila <Tipoequipos, 50> &PilT)
{
    while(!Tiquipos.Vacia()){
        Tiquipos.Remover(Equipos);
    if (Equipos.tipo=="El"){
        PilEl.Insertar(Equipos);
    }
     if (Equipos.tipo=="Ed"){
        PilEd.Insertar(Equipos);
    }
     if (Equipos.tipo=="T"){
        PilT.Insertar(Equipos);
    }
      
        
  /* 
    while(!PilEl.Vacia() && !PilEd.Vacia() && !PilT.Vacia()){
      PilEl.Remover(Equipos);
      Tiquipos.Insertar(Equipos);
      PilEd.Remover(Equipos);
      Tiquipos.Insertar(Equipos);
      PilT.Remover(Equipos);
      Tiquipos.Insertar(Equipos);
    };

   */
} 
    cout<<"\nLos equipos se han clasificado correctamente"<<endl;
  }
   
     void Descuentos(Pila <Tipoequipos, 50> &PilaAux, Pila <Tipoequipos, 50> &PilEl,Pila <Tipoequipos, 50> &PilEd,Pila <Tipoequipos, 50> &PilT){
         
         
         
      int i;   
      
      while(!PilEl.Vacia() && !PilEd.Vacia() && !PilT.Vacia()){
          
      if(Equipos.tipo=="El"){
          
       PilEl.Remover(Equipos);
      Equipos.descuento = Equipos.Precio - (Equipos.Precio * 0.10); 
       PilaAux.Insertar(Equipos);
      
       i=0;
       while(!PilaAux.Vacia()){
           PilaAux.Remover(Equipos);
           PilEl.Insertar(Equipos);
      
           i++;
       }
       
       
      }//fin if   
      
     if(Equipos.tipo=="Ed"){
          
       PilEd.Remover(Equipos);
      Equipos.descuento = Equipos.Precio - (Equipos.Precio * 0.09); 
       PilaAux.Insertar(Equipos);
      
       i=0;
       while(!PilaAux.Vacia()){
           PilaAux.Remover(Equipos);
           PilEd.Insertar(Equipos);
      
           i++;
       }
       
       
      }//fin if   
      
      
      if(Equipos.tipo=="T"){
          
       PilT.Remover(Equipos);
      Equipos.descuento = Equipos.Precio - (Equipos.Precio * 0.07); 
       PilaAux.Insertar(Equipos);
      
       i=0;
       while(!PilaAux.Vacia()){
           PilaAux.Remover(Equipos);
           PilT.Insertar(Equipos);
      
           i++;
       }
       
     
      }//fin if   
      
     
    };//FIN WHile
         
         
         
         
       cout<<"\nLos descuentos fueron aplicados correctamente"<<endl; 
     }


     
  void Imprimir(Pila <Tipoequipos, 50> &Tiquipos,Pila <Tipoequipos, 50> &PilaAux)
      {
    i=-1;
    while(!Tiquipos.Vacia()){
        Tiquipos.Remover(Equipos);
        PilaAux.Insertar(Equipos);
    };
    while(!PilaAux.Vacia()){
        PilaAux.Remover(Equipos);
    
     i++;
     cout<<"\n-------------------------------------------------------------------"<<endl;
        cout<<"EQUIPO #"<<i+1<<endl;
        cout<<"Codigo del equipo:"<<Equipos.codigo;
        cout<<endl<<"Nombre del Equipo:"<<Equipos.Nombre;
         cout<<endl<<"Tipo de equipo:"<<Equipos.tipo;
         cout<<endl<<"La cantidad es :"<<Equipos.cantidad;
         cout<<endl<<"El precio es :"<<Equipos.Precio;
         Tiquipos.Insertar(Equipos);
};
      }
  
  void ImprimirClasificados(Pila <Tipoequipos, 50> &PilaAux, Pila <Tipoequipos, 50> &PilEl,Pila <Tipoequipos, 50> &PilEd,Pila <Tipoequipos, 50> &PilT){     
      int i=0;
      while(!PilEl.Vacia() && !PilEd.Vacia() && !PilT.Vacia()){
      PilEl.Remover(Equipos);

     cout<<"\n-------------------------------------------------------------------"<<endl;
        cout<<"EQUIPO #"<<i+1<<endl;
        cout<<"Codigo del equipo:"<<Equipos.codigo;
        cout<<endl<<"Nombre del Equipo:"<<Equipos.Nombre;
         cout<<endl<<"Tipo de equipo:"<<Equipos.tipo;
         cout<<endl<<"La cantidad es :"<<Equipos.cantidad;
         cout<<endl<<"El precio es :"<<Equipos.Precio;
      cout<<endl<<"El precio con descuento es :"<<Equipos.descuento;
      
      PilEd.Remover(Equipos);
     cout<<"\n-------------------------------------------------------------------"<<endl;
        cout<<"EQUIPO #"<<i+1<<endl;
        cout<<"Codigo del equipo:"<<Equipos.codigo;
        cout<<endl<<"Nombre del Equipo:"<<Equipos.Nombre;
         cout<<endl<<"Tipo de equipo:"<<Equipos.tipo;
         cout<<endl<<"La cantidad es :"<<Equipos.cantidad;
         cout<<endl<<"El precio es :"<<Equipos.Precio;
      cout<<endl<<"El precio con descuento es :"<<Equipos.descuento;
      
      PilT.Remover(Equipos);
       
     cout<<"\n-------------------------------------------------------------------"<<endl;
        cout<<"EQUIPO #"<<i+1<<endl;
        cout<<"Codigo del equipo:"<<Equipos.codigo;
        cout<<endl<<"Nombre del Equipo:"<<Equipos.Nombre;
         cout<<endl<<"Tipo de equipo:"<<Equipos.tipo;
         cout<<endl<<"La cantidad es :"<<Equipos.cantidad;
         cout<<endl<<"El precio es :"<<Equipos.Precio;
      cout<<endl<<"El precio con descuento es :"<<Equipos.descuento;
      
      i++;
    };
    
  }

    

int main(){
    do
	{
		cout<<"\n----------------------------Menu-----------------------------------    \n\n";
		cout<<"     1. Cargar datos de equipos\n";
		cout<<"     2. Clasificar equipos por tipos \n";
		cout<<"     3. Realizae descuantos por tipos\n";
		cout<<"     4. Imprimir Datos de los Equipos \n";
                cout<<"     5. Imprimir Datos de los Equipos Clasificados \n";
		cout<<"     6. Salir\n\n";
		cout<<"-------------------------------------------------------------------    \n";
		cout<<"           Seleccione su opcion: ";
		cin >> opc;
		cout << endl;
		switch(opc)
		{
			case 1: CargarPila(Tiquipos);
			         system("clear");
                        break;
			case 2: Clasificar(Tiquipos,PilEl,PilEd,PilT);
			        break;
			case 3: Descuentos(PilaAux,PilEl,PilEd,PilT);
                         system("clear");
			        break;
			case 4: Imprimir(Tiquipos , PilaAux);
			        break;
                                
                                
                    case 5: ImprimirClasificados(PilaAux,PilEl,PilEd,PilT);
                         system("cls");
                        break;
                    
			case 6: 
                             system("clear");
                            return 0;
                                
                        system("clear");
		
			default: cout<<"Error, Selccione de nuevo\n\n\n";		
			
		}
	}while(opc!=6);
    

    return 0; }
