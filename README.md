# 01.Abril.16
### Normalmente se utiliza el modelo aditivo... Este modelo es apropiado cuando la magnitud de las fluctuaciones estacinales de la serie no varia al hacerlo la tendencia.
### SE UTILIZA MULTIPLICATIVO
### Cuando la magnitud de las fluctuaciones estacionales de la serie crece y decrece proporcionalmente con los crecimientos y decrecimientos de la tendencia, respectivamente.
### Una vez que logramos descomponer la st en diversos los elementos de estacionalidad y tendencia hay que 
#desestacionalizar la st y eliminar la tendencia
### Existe TENDENCIA cuando existe un patron en los datos a largo plazo ya sea que aumenta o disminuye los datos.
### La estacionalidad existe cuando la st cuando es influenciado por factores estacionales (por ejemplo, la trimestre del año, el mes, o el dia de la semana).
### Existen componente de ciclicos en los datos cuando se detectan incrementos y caídas que no son de tiempo determinado (duracion por lo general de al menos 2 años).

### 3 de estos 3 elementos normalmente existen confusiones para detectarlos entre la estacionalidad y el componente ciclico
### Principales diferencias entre estos dos componentes
### 1) Patron estacional longitud constante; patron ciclico longitud variable
### 2) Duracion media del componente ciclico mas largo que la longitud del patron estacional
### 3) Magnitud de ciclico mas variable que magnitud del patron estacional
### 4) El momento de picos y caidas es predecible con los datos estacionales, pero impredecible a largo plazo con datos ciclicos.

install.packages("fpp")
require (fpp)
help(fpp)
plot(window(elec,start=1980),ylab="GWh",xlab="Year",main="Australian electricity production")
### ESTACIONALIDAD, TENDENCIA Y CICLICO
plot(bricksq,ylab="million units",xlab="Year",main="Australian clay brick production")
### ESTACIONALIDAD Y CICLO, NO MUCHA TENDENCIA
plot(hsales,main="Sales of new one-family houses, USA",ylab="Total sales",xlab="Year")
### NO HAY TENDENCIA,TAMPOCO ESTACIONALIDAD Y POSIBLE CICLO
### 3EJEMPLOS GRAFICAS DETECTAR TENDENCIA, ESTACIONALIDAD Y CICLO     
ap <- read.csv ("C:\\Users\\SALA-C13\\Desktop\\app.csv", header = T)
apts <- ts(ap [ , 5],start= 2000, frequency = 12)
plot(apts, main="Valor de acciones apple", ylab= "Valor cierre", xlab="Años")
### Existe una estacionalidad en el periodo 2000-2006 ya que sus acciones se mantuvieron en un precio constante, para el año 2007 a 2014 se mostro una tendencia a la alza en los precios de
#sus acciones , y un posible ciclo en el año 2014.

intel <- read.csv ("C:\\Users\\SALA-C13\\Desktop\\inte.csv", header =T)
ints <- ts(intel [ , 5], start= 2000, frequency = 12)
plot(ints)
plot(ints,main="Valor de acciones intel", ylab= "Valor cierre", xlab="Años")
### Se muestra que en los primeros años existe un ciclio, no existe tendencia y posiblemente existe estacionalidad, que puede ser relacionada que por la competencia de las demas marcas como apple, se mantuvieran asi.

mic <- read.csv ("C:\\Users\\SALA-C13\\Desktop\\mic.csv", header = T)
mits <- ts(mic [ , 5], start= 2000, frequency = 12)
plot(mits, main="Valor de acciones microsoft ", ylab= "Valor cierre", xlab="Años")
### Del año 2000-2003 existen quizas dos ciclos, despues una posible estacionalidad igual posiblemente relacionada con la competencia.

jpeg(filename = "acciones.jpg")##la imagen la guarda en doc
layout(1:3)
plot(apts, main="Valor de acciones apple", ylab= "Valor cierre", xlab="Años")
plot(ints,main="Valor de acciones intel", ylab= "Valor cierre", xlab="Años")
plot(mits, main="Valor de acciones microsoft ", ylab= "Valor cierre", xlab="Años")
dev.off()
