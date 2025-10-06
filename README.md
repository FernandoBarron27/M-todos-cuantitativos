#Andrés_Fernando_Wilma_Denisse
#Métodos_cuantitativos
#Modelos_MULTINOMIALES
-----------------------------------------------------------------------------
# Instalar paquetes si no los tienes
install.packages("readxl")
install.packages("nnet")
install.packages("marginaleffects")
install.packages("dplyr")

# Cargar librerías
library(readxl)
library(nnet)
library(marginaleffects)
library(dplyr)
list.files()
# Cargar archivo Excel (ajusta la ruta a donde lo tengas guardado)
data <- read_excel("BASE NOMINAL1.xlsx")

# Ver estructura
head(data)
str(data)

# Ajustar modelo multinomial
modelo <- multinom(Apoyo.a.la.democracia ~ Edad + Sexo + Confianza.en.el.Gobierno, data = data, trace = FALSE)

# Resultados
summary(modelo)

# Odds ratios
exp(coef(modelo))

## Efectos marginales

ame_Edad <- avg_slopes(modelo, variables = "Edad", type = "probs")
ame_Edad

ame_Sexo <- avg_slopes(modelo, variables = "Sexo", type = "probs")
ame_Sexo

ame_Confianza.en.el.Gobierno <- avg_slopes(modelo, variables = "Confianza.en.el.Gobierno", type = "probs")
ame_Confianza.en.el.Gobierno
