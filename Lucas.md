# Charla Ing. de software

_By Andrés Goméz_
Ordenadores cuánticos -> ai -> Machine learning

La relación entre ellos, y lo que esta haciendo el cesga relacionado sobre ello. Y como va a avanzar esto en términos de Galicia

## Cesga
- Mision -> contrivuir al avance de la ciencia y conocimiento tecnico, buscar the high performance computing and communications. Es público, y buscan la mejora de la sociedad. 
- Los servicios que dan son una tecnología capaz de adaptarse a las necesidades de los investigadores de muchas áreas de conocimiento
- Formada por ingenieros, informaticos, fisicos, matemáticos ...
- Trabajan actualmente 47 personas

### Desafías actuales y a futuro

- Big Data
- Machine learning, and DL; Modelos que necesitan una gran red de computación para ser entrenados
- A futuro Computacion cuantica y comunicaciones
### Infraestructura
Finis Ferrae III
714 procesadores intel xeon
157 GPUS
126TB memory
359TB NVME
Storage: 5PB (HDDs + SSDs)... y muxo más
### Quantum computing?
Fue propuesto en 1980 el tema "computación cuántica" -> Richard Feynman
Propusieron la existencia del qubit (Los 70)
qbit
Llegan a temperaturas cercanas a 0k

##### Definición posible
La computación mécanica es una rama de la computación que usa los principios de la fisica cuántica para calcular o computar
#### La unidad básica de esta computación es el qubit
Tiene dos posibles estados, 0 o 1. Podemos elegir a que llamar que. "A quantum system with two eigenstates that can be manipulated arbitrarly" ->
Sistema cuantico que cuando lo mezclamos nos puede dar dos posibles resultados, con una cierta probabilidad cada uno. Los cuales podemos definir como los clasicos 0 y 1 de los bits. Los cuales podemos manipular para cambiar estás probabilidades
#### Some models of quantum computing
- Simulador cuántico -> uso de sistema cuantico en un sistema análogico
- Adiabatic quantum computer (No lo tiene el Cesga) -> construido para resolver cosas de optimización y resolución de problemas
- Topological quanting computer -> propiedades topólogicas y está a futuro
- Continuos Variable Quantum Computer
- Universal Quantum Computer -> Es demostrable que cualquier operación es teoricamente posibles en el
- Digital-analogico ordenador cuantico
#### No están siendo creados para reemplazar a los ordenadores personales, son para la creación de nuevos algoritmos; son útiles para la resolucion de ciertos problemas
#### Posibles ventajas que aún estan por demostrar
- Resolver problemas que serían muy dificiles de resolver a la clásica (romper claves ssh)
- Obtener una mejor solucion algoritmica que la clásica
- Quantum machine learning
- Obtener soluciones similares o equivalentes en menor tiempo
- Peores soluciones pero menor gasto de energía
#### Todos los algoritmos son hibrídos
- Puede que los algoritmos cuánticos estén limitados por la computación clásica

#### Types of quantum computers
- Superconductores
- Fotonicos
- Iones atrapados
- Spin Cubit
- Atom Arrays
- NV centros en diamantes
- Majorana ...

#### Divincenzo's criteria
1. Un sistema fisico escalable caracterizado pro los qubits
2. Habilidad de iniciar los qubits como simples "fiat state" como 000000 >
3. Long relevant decoherence times, mas largos que la operación de celda ?
4. A "universal " set of quantum gates
5. Sistema especifico de medida de capacidad de los qubits
#### Fisicas
Puedes usar algo inicial como un atomo para un sistema cuántico, o empezarlo de cero
#### Qubit. Mathematics
Pedir esto (Algo como la superposición con vectores de numeros complejos que al cuadrado te dan si es 0 o 1)
Si se mide un 1 y se vuelve a medir un 1 se estara al 100% que a la siguiente será un 1
rellenar esta parte con capturas de las diapositivas

#### Cómo los manipulamos realmente
Se tranforman las matrices en una operación física

### More than  one qubit
La única diferencia es que ahora hay un vector mas grande, se va multiplicando por dos

$[00] =$ 
| 1   |
| --- |
| 0   |
| 0   |
| 0   |


Classical information can be mapped to:
_No me dió tiempo_

**Un sistema con 270 qubits podrían acumular $4*10^(81)$ real numbers **

##### Entanglement
Cuando el estado de dos o más qubits no puede ser separado en sus componentes individuales
Matemáticamente el estado no es factorizable

#### Operaciones controladas
- Apply an operation on a qubit or set of qubits depending of the value of the qubit or several qubits ( without meausuring them)
- _No copié lo último ni lo siguiente_
#### programación
se hace primariamente en assmemble pero hay diferentes librerías, de alto nivel para diferentes areas, ya sea quimica, finanzas etc.
Https://algassert.com/quirk    -> para jugar? xd
## Machine learning


## Big Data

## IA


## Relation between computación cuantica e Inteligencia Artificial
Una red neuronal sería equivalente al VQE?

#### Parametric Quantum Citcuits
No se piensa en el problema fisico, sino el computacional
Dependiend del input tendré cierto output (Number of qubits)

##### Types ?
- Quantum Neural Networks
- Quantum Recurrent Neural Networks
- Variational Quantum Factorization
- Variatonal Quantum Linear Solver
- And more
##### Difficulties of PQC
- Optimitation -> Multiple local minimals, barren plateaus, numerical gradients, periodicity
- _No lo copié jjj_
- Noise in the calculations

#### Quantum Recurrent Neural Netwoeks for Multivariate Time Series Prediction

- Use intermediate measurments to exxtract information
- Using additional qubits (without measurement) to keep memory
###### Goals
- To predict one time-series usando n veces series
- Aplicar el algoritmo a problemas reales de la industria
- Mejorar los optimizadores de estos algoritmos

## Trabajos que esta haciendo un investigador en la coruña
_No ce_

### Other IA & QC
- Quantum principal component
- _No copié los demás
- 
### Hay algún ordenador cuantico para TFG
SIII
Tiene una capacidad de 32 qubits
El sistema está aíslado para su mejor refrigeración

### Simulación cuántica 
- 
#### To acces an hour to the IBM system, it costs 20.000 - 50.000$

No se programa exactamente en ensamblador, es similar porque se trabaja a nivel de qubit, suele usarse python
