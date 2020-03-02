metodos numericos

import matplotlib.pyplot as plt
import numpy as np


import numpy
m=int(input('Valor de m:'))#renglones=m
n=int(input('Valor de n:'))#Columnas=n
matrix= numpy.zeros((m,n))
x=numpy.zeros((m))

vector=numpy.zeros((n))
comp=numpy.zeros((m))
error=[]

print('Metodo de Gauss-Seidel')
print('Introduce la matriz de coeficientes y el vector solucion')
for r in range(0,m):
  for c in range(0,n):
    matrix[(r),(c)]=float(input("Elemento a["+  str(r+1)+str(c+1)+"]"))
  vector[(r)]=float(input('b['+str(r+1)+']:'))
tol=float(input("¿Cual es la tolerancia que deseas? "))
itera=int(input("¿Cual es el numero maximo de iteraciones? "))
#metodo de gauss seidel

k=0
while k<itera: #agregar
  suma=0
  k=k+1
  for r in range (0,m):
    suma=0
    for c in range (0,n):
      if (c!=r):
        suma=suma+matrix[r,c]*x[c]
    x[r]=(vector[r]-suma)/matrix[r,r]

    print("x["+str(r)+"]:"+str(x[r]))
  del error[:]
  #Comprobacion
  for r in range (0,m):
    suma=0
    for c in range (0,n):
        suma=suma+matrix[r,c]*x[c]
        comp[r]=suma
        dif=abs(comp[r]-vector[r])
        error.append(dif)
        print("Error en x [",r,"]= ",error[r])
  print("Iteraciones:" ,k)
  if all (i<=tol for i in error) == True:
       break   
lista1 = ([r])
plt.plot(lista1)
plt.show() 

print ("Hasta luego") 
