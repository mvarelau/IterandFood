# IterandFood
Aquí el repo del reto #7
## Aqui está el codigo de el restaurante al que se le agregó la clase Pedido iterable
Tiene la capacidad de volver un conjunto de pedididos ingresados en un iterable
```python
class MenuItem:
    def __init__(self,name:str,price:float, description:str):
        self.name = name
        self.price = price
        self.description = description

class Veberage(MenuItem):#Kind is cold or hot 
    def __init__(self,name:str,price:float, description:str, Kind=str):
        super().__init__(name,price,description)
        self.Kind=Kind 

class BreakFast(MenuItem):
    def __init__(self,name:str,price:float, description:str, Flavor:str):
        super().__init__(name,price,description)
        self.flabour= Flavor

class Lunch(MenuItem):#Kind is for example, executive, current or menu 
    def __init__(self,name:str,price:float, description:str, protein:str):
        super().__init__(name,price,description)
        self.protein=protein


class Order:
    def __init__(self, item:MenuItem, Order_list):
        self.item=item
        self.Order_list=Order_list

    def Totall_Amount(self, Order_List):       
        Price_List=[]
        for x in Order_List:
            i = x.price
            Price_List.append(i)
        suma=sum(Price_List)
        return suma 
    def apply_discounts(self,Order_List):
        Total_amount= Order.Totall_Amount(Order,Order_List=Order_List)
        if len(Order_List)>=4:
            Total_amount= Total_amount-(Total_amount*0.01)
            print(Total_amount)
        else:
            print("You dont have a discount")
    
    
# Implementación en español del iterador para los elementos de un pedido.

class PedidoIterable:
    """
    Clase que permite iterar sobre los elementos de un pedido.
    """
    def __init__(self, lista_pedidos):
        """
        Inicializa la clase con una lista de elementos de pedido.
        :param lista_pedidos: Lista que contiene los elementos del pedido (objetos de tipo MenuItem).
        """
        self.lista_pedidos = lista_pedidos
        self.indice = 0  # Inicializa el índice en 0 para comenzar la iteración desde el primer elemento.

    def __iter__(self):
        """
        Método que devuelve el objeto iterador (en este caso, a sí mismo).
        :return: Devuelve el propio objeto para ser usado en iteraciones.
        """
        return self

    def __next__(self):
        """
        Método que devuelve el siguiente elemento de la lista en cada iteración.
        :return: Devuelve el siguiente elemento en la lista de pedidos.
        """
        if self.indice < len(self.lista_pedidos):
            pedido = self.lista_pedidos[self.indice]
            self.indice += 1  # Incrementa el índice para la siguiente llamada
            return pedido
        else:
            raise StopIteration  # Lanza esta excepción cuando se han recorrido todos los elementos.


# Actualizamos el archivo Restaurant.py para que sea posible iterar sobre los pedidos
# Vamos a agregar la nueva clase al script

codigo_actualizado = restaurant_code + """

# Implementación de la clase PedidoIterable para permitir iteraciones sobre los pedidos
if __name__ == "__main__":
    # Creamos un ejemplo de varios pedidos
    pedidos = [
        Veberage(name="Strawberry Juice", price=5, description="Refrescante jugo de fresa.", Kind="Frío"),
        BreakFast(name="Pancakes", price=7, description="Deliciosos pancakes con sirope.", Flavor="Dulce"),
        Lunch(name="Filete de pollo", price=10, description="Filete de pollo con arroz y ensalada.", protein="Pollo")
    ]

    # Crear instancia del iterador
    iterador_pedidos = PedidoIterable(pedidos)

    # Iteramos sobre los pedidos e imprimimos sus atributos
    for pedido in iterador_pedidos:
        print(f"Nombre: {pedido.name}, Precio: {pedido.price}, Descripción: {pedido.description}")
"""

# Guardamos el nuevo código actualizado en un archivo para que el usuario lo pueda descargar.
output_file_path = '/mnt/data/Restaurant_Actualizado.py'
with open(output_file_path, 'w') as output_file:
    output_file.write(codigo_actualizado)

output_file_path



if __name__=="__main__":
#Create menu 
#VEBERAGE 
#Cold Veberage: 
    Strawberry =Veberage(name="Straberry Juice", price=5,
                     description="Get inspired by the fresh taste of Strawberry Juice, Cold and refreshing.", Kind="Cold")
    Mango= Veberage(name="Mango Juice", price= 5, 
                description="Get inspired by the fresh flavor of Jugo Mago, cold and refreshing.",Kind="cold" )
    Lemonade= Veberage(name="Normal Lemonade", price=4, 
                             description="Feeling dry? A Lemonade is the best chioce", Kind="Cold")
    Coco_Lemonade=Veberage(name="Coco Lemonade", price=4, 
                                 description="Feeling dry? A Coco Lemonade is the best chioce to feel fresh",Kind="Cold")
    Cocacola= Veberage(name="Cocacola", price=5,
                     description="Iced Coke", Kind="Cold")

#Hot Veberage
    Coffe= Veberage(name="Coffe", price=4,
                     description="Perfect to digest an exelent luch", Kind="Hot")
    Tea=Veberage(name="Hot Tea", price=4,
                     description="Perfect to relax after lunch", Kind="Hot")
    Chocolat=Veberage(name="Hot Chocolate", price=6,
                     description="Hot chocolate with marshmallows to be cozy", Kind="Hot")


# Breakfast
    Sirup_pancakes= BreakFast(name="Sirup_Pancakes", price=15,
                     description="Sirup pancakes with fruit", Flavor="Sweet")
    
    Nutella_pancakes = BreakFast(name="Nutella_Pancakes", price=15,
                     description="Nutella pancakes with fruit", Flavor="Sweet")
    
    eggs=BreakFast(name="Eggs", price=13,
                     description="Beaf creps with cheese", Flavor="Salty")
    
#Lunch
    beaf_creps=Lunch(name="Beaf Creps", price=13,
                     description="Nutella pancakes with fruit", protein="Beaf")
    
    ham_creps=Lunch(name="Ham creps", price=13,
                     description="Nutella pancakes with fruit", protein="Ham")
    
#Create order
    First_Order:Order=[Strawberry,Coffe, Nutella_pancakes]
    Price= Order.Totall_Amount(Order, First_Order)
    


    Second_Order:Order=[Cocacola,Chocolat,Sirup_pancakes,eggs]
    Price= Order.apply_discounts(Order,Second_Order)
    print(Price)







    



    

    
        


        

    

        
        
        
        
        
            








# Implementación de la clase PedidoIterable para permitir iteraciones sobre los pedidos
if __name__ == "__main__":
    # Creamos un ejemplo de varios pedidos
    pedidos = [
        Veberage(name="Strawberry Juice", price=5, description="Refrescante jugo de fresa.", Kind="Frío"),
        BreakFast(name="Pancakes", price=7, description="Deliciosos pancakes con sirope.", Flavor="Dulce"),
        Lunch(name="Filete de pollo", price=10, description="Filete de pollo con arroz y ensalada.", protein="Pollo")
    ]

    # Crear instancia del iterador
    iterador_pedidos = PedidoIterable(pedidos)

    # Iteramos sobre los pedidos e imprimimos sus atributos
    for pedido in iterador_pedidos:
        print(f"Nombre: {pedido.name}, Precio: {pedido.price}, Descripción: {pedido.description}")
```
