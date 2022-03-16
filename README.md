# R2-D2 Modelo en Blender 2.8
En este repositorio he creado un modelo 3D en Blender a partir de un script en python.
Subiré el avance día a día en el proyecto.

## Dia 1
Empecé con la parte más sencilla, el pecho. Consta de una cabeza esférica y un cilindro. 
En este día me he familiarizado con la API y trasteado con algunas funciones. 
Esto he logrado:
![dia1](/dia1.PNG)

## Dia 2
Implementé una funcion para substraer 1 cuerpo mediante otro llamado herramienta. Esta función es muy útil
ya que puedo crear formas más allá de las básicas.
~~~
class OperacionBinaria:
    
    def diferencia(objName, objNameTool):
        objeto = bpy.data.objects[objName]
        herramienta = bpy.data.objects[objNameTool]
        mod = objeto.modifiers.new("Boolean", type='BOOLEAN')
        mod.operation = 'DIFFERENCE'
        mod.object  = herramienta
        bpy.context.view_layer.objects.active = objeto
        
        bpy.ops.object.modifier_apply(apply_as='DATA', modifier=mod.name)
        bpy.data.objects.remove(herramienta)
        
    def unir(lista, nuevo_nombre):
        seleccionarVarios(lista)
        bpy.ops.object.join()
        bpy.context.view_layer.objects.active.name = nuevo_nombre
~~~

Un ejemplo, es el detalle que tiene bajo el pecho. Es una sección de cono que busca asemejarse a la parte baja de
R2 donde guarda su tercer pie.
Le añadí un ojo más realista y le creé dos brazos simples que posteriormente se modificarán para hacerlos
más detallados.
![dia2](/dia2.PNG)

## Dia 3
Añadí una funcion para hacer un join de varios elementos. En conjunto con la función de substraer, se puede crear
casi cualquier cosa. 
Le añadí pies y modifiqué la forma para tratar de ser mas fiel al original.
Los pies constan de una figura "cubo" escalada para estirarla. Usando la función de sustraer logro hacer que tenga forma
trapecioidal. Además a modo de detalle, le he añadido 3 ruedas a cada pie.
Otro detalle, es el tercer pie que se ve retraido en el bajo pecho ya que R2 está modelado en su posición de solo dos pies.
![dia3](/dia3.PNG)

## Dia 4 (Finalizado)
Ahora queda añadir unas texturas al modelo generado para poder obtener un render bonito del modelo. 
Además le damos un fondo plateado a la cabeza ya que es metálica.
Escojemos un ángulo de cámara bonito, una buena luz y está listo para el renderizado.
![dia4](/RENDER.png)
