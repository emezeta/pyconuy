Propuesta de llamado a charlas PyCon.Uy 2012:


- TODO: ...

- ing: texto RFC web - inglés
- esp: español

- call4speakers-eng: borrador para apertura del llamado - inglés
-	call4speakers-es: español 	

-	announce-en: spam para las masas - inglés
- anuncio-es: español

- readme.rst: este archivo



*Métodos de instancia*

Cuando se crea un método de instancia, el primer parámetro es siempre self. Puedes nombrarlo como quieras, pero el significado siempre será el mismo, y deberías usar self ya que es la convención de nombres. self es (usualmente) pasado de forma oculta cuando se llama a un método de instancia; representa la instancia que llama al método.

He aquí un ejemplo de una clase llamada Inst que tiene un método de instancia llamado introduce():

::
    class Inst:

        def __init__(self, name):
            self.name = name

        def introduce(self):
            print("Hello, I am %s, and my name is " %(self, self.name))


Ahora, para llamar a este método, primero necesitamos crear una instancia de nuestra clase. Una vez que tenemos una instancia, podemos llamar a introduce() en ella, y la instancia será automáticamente pasada como self:

::
    myinst = Inst("Test Instance")
    otherinst = Inst("An other instance")
    myinst.introduce()
    # outputs: Hello, I am <Inst object at x>, and my name is Test Instance
    otherinst.introduce()
    # outputs: Hello, I am <Inst object at y>, and my name is An other instance



Como ves, no estamos pasando el parámetro self, sino que se pasa de forma oculta con el operador "." estamos llamando a ”intoduce()”, método de instancia de la `clase Inst`, con el parámetro de myinst u otroinst. Esto significa que podemos llamar a Inst.introduce(myinst) y obtener exactamente el mismo resultado.


*Métodos de clase*

La idea del método de la clase es muy similar al método de la instancia, con la única diferencia de que en lugar de pasar la instancia de forma oculta como un primer parámetro, ahora estamos pasando la clase misma como un primer parámetro.

::
    class Cls:

        @classmethod
        def introduce(cls):
            print("Hello, I am %s!" %cls)

Ya que estamos pasando sólo una clase al método, no hay ninguna instancia involucrada. Esto significa que no necesitamos una instancia en absoluto, llamamos al método de la clase como si fuera una función estática:

::
    Cls.introduce() # same as Cls.introduce(Cls)
    # outputs: Hello, I am <class 'Cls'>

Note que de nuevo Cls se pasa de forma oculta, por lo que también podríamos decir `Cls.introduce(Inst)` y obtener la salida "Hello, I am <class 'Inst'>. Esto es particularmente útil cuando estamos heredando una clase de Cls:

::
    class SubCls(Cls):
        pass

    SubCls.introduce()
    # outputs: Hello, I am <class 'SubCls'>
